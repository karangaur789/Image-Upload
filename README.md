 public async Task<ActionResult> Index(IFormFile file)
        {
            try
            {
                //var result = new StringBuilder();
                //using (var reader = new StreamReader(file.OpenReadStream()))
                //{

                //    while (reader.Peek() >= 0)
                //    {
                //        result.AppendLine(await reader.ReadLineAsync());
                //    }
                //    byte[] imageArray = System.IO.File.ReadAllBytes(file.FileName);
                //    string base64ImageRepresentation = Convert.ToBase64String(imageArray);
                //}



                using (var memoryStream = new MemoryStream())
                {
                    await file.CopyToAsync(memoryStream);
                    byte[] fileBytes = memoryStream.ToArray();
                    string base64ImageRepresentation = Convert.ToBase64String(fileBytes);

                }
                }
            catch (Exception ex)
            {

            }
            return View("Index");
        }



        ///////
        <form method="post" enctype="multipart/form-data">
    <input type="file" name="file" />
    <button type="submit">Upload File</button>
</form>
