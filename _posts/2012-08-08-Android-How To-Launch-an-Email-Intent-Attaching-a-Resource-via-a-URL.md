---
layout: post
title: Android - How To Launch an Email Intent Attaching a Resource via a URL

redirect_from:
  - /blog/android-how-to-launch-an-email-intent-attaching-a-resource-via-a-url/
---

Today at work I had the requirement to invoke an intent that would send a plain text email but with an **image attachment sourced from the internet**. I struggled to find a complete solution online for these particular requirements and thought I’d share my solution here.


{% highlight java %}

String urlOfImageToDownload = "https://ssl.gstatic.com/s2/oz/images"
    + "/google-logo-plus-0fbe8f0119f4a902429a5991af5db563.png";
String attachmentFileName = "AnImageFromTheWeb.png";
 
// Start to build up the email intent
Intent i = new Intent(Intent.ACTION_SEND);
i.setType("message/rfc822");
i.putExtra(Intent.EXTRA_EMAIL, new String[] { "abc@mail.com" });
i.putExtra(Intent.EXTRA_SUBJECT, "Check Out This Image");
i.putExtra(Intent.EXTRA_TEXT, "There should be an image attached");
 
// Do we need to download and attach an icon and is the SD Card available?
if (urlOfImageToDownload != null && Environment.MEDIA_MOUNTED.equals(
        Environment.getExternalStorageState())) {
    // Download the icon...
    URL iconUrl = new URL(urlOfImageToDownload);
    HttpURLConnection connection
        = (HttpURLConnection) iconUrl.openConnection();
    connection.setDoInput(true);
    connection.connect();
    InputStream input = connection.getInputStream();
    Bitmap immutableBpm = BitmapFactory.decodeStream(input);
 
    // Save the downloaded icon to the pictures folder on the SD Card
    File directory = Environment.getExternalStoragePublicDirectory(
        Environment.DIRECTORY_PICTURES);
    directory.mkdirs(); // Make sure the Pictures directory exists.
    File destinationFile = new File(directory, attachmentFileName);
    FileOutputStream out = new FileOutputStream(destinationFile);
    immutableBpm.compress(Bitmap.CompressFormat.PNG, 90, out);
    out.flush();
    out.close();
    Uri mediaStoreImageUri = Uri.fromFile(destinationFile);    
 
    // Add the attachment to the intent
    i.putExtra(Intent.EXTRA_STREAM, mediaStoreImageUri);
}                      
 
// Fire the intent
startActivity(i);

{% endhighlight %}