```
FileUploadServlet.java
    try {
        out = new FileOutputStream(new File(path + File.separator + fileName));;
        filecontent = filePart.getInputStream();

        int read;
        final byte[] bytes = new byte[1024];

        while ((read = filecontent.read(bytes)) != -1) { out.write(bytes, 0, read); }
        writer.println("New file " + fileName + " created at " + path);
        LOGGER.log(Level.INFO, "File {0} being uploaded to {1}",
            new Object[]{fileName, path});
    } catch (FileNotFoundException fne) {
        writer.println("You either did not specify a file to upload or are "
            + "trying to upload a file to a protected or nonexistent "
            + "location.");
        writer.println("<br/> ERROR: " + fne.getMessage());
        LOGGER.log(Level.SEVERE, "Problems during file upload. Error: {0}",
            new Object[]{fne.getMessage()});
    } finally {
        if (out != null) { out.close(); }
        if (filecontent != null) { filecontent.close(); }
        if (writer != null) { writer.close(); }
    }
}
```