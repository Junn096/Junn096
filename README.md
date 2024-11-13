<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>File Upload</title>
</head>
<body>
    <h2>File Upload Form</h2>
    <form action="upload.php" method="POST" enctype="multipart/form-data">
        <input type="file" name="fileToUpload" required>
        <br><br>
        <button type="submit">Upload File</button>
    </form>
</body>
</html>
<?php
// Uploads folder ka path
$targetDir = "uploads/";
$targetFile = $targetDir . basename($_FILES["fileToUpload"]["name"]);
$uploadOk = 1;
$fileType = strtolower(pathinfo($targetFile, PATHINFO_EXTENSION));

// File size check (5 MB limit)
if ($_FILES["fileToUpload"]["size"] > 5000000) {
    echo "File size 5MB se zyada hai.";
    $uploadOk = 0;
}

// Allow only certain file types (sirf JPG, PNG, GIF, PDF)
if ($fileType != "jpg" && $fileType != "png" && $fileType != "jpeg" && $fileType != "gif" && $fileType != "pdf") {
    echo "Sirf JPG, JPEG, PNG, GIF aur PDF files allowed hain.";
    $uploadOk = 0;
}

// Check if $uploadOk is 0 (error) or 1 (success)
if ($uploadOk == 0) {
    echo "File upload nahi ho sakti.";
} else {
    if (move_uploaded_file($_FILES["fileToUpload"]["tmp_name"], $targetFile)) {
        echo "File " . htmlspecialchars(basename($_FILES["fileToUpload"]["name"])) . " upload ho gayi hai.";
    } else {
        echo "File upload karte waqt error aaya.";
    }
}
?>
