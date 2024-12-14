<h1 align="center"> 
  Linux in daily use </h1>
<div align="center">
  <a href="https://github.com/kabyadeb/">
      Follow on Github
    </a>

</div>
To update

```
sudo apt update
```
Remove unused packages:
```
sudo apt autoremove --purge
```
Clear old kernels (be careful with this):
```
sudo apt --purge autoremove
```
Clean up package cache:
```
sudo apt clean
```
 Check your current swap size with RAM:
 ```
free -h
```

#### Question 1 : Can we marge multiple PDFs in ubuntu through terminal ?
The answer is Yes. 
there are multiple tools we can use. Here I will discuss about `poppler` tool.
A PDF rendering library that includes a command-line tool called pdfunite. Install it using 
(Debian-based)
```
sudo apt install poppler-utils
```
 or (RPM-based)
```
sudo dnf install poppler-utils
```
After installing we are prepared to marge files.
Example command: `pdfunite input1.pdf input2.pdf output.pdf`

#### Question 2 : Can we connect or access internet in recovery mode on Ubuntu ?
Here is my answer 
[Connecting to a Wi-Fi network in recovery mode on Ubuntu](https://github.com/kabyadeb/linux_debian/blob/main/connect%20wifi%20in%20recovery%20mode.md)

#### Question 3 : How to trim pdf into specific pages on Ubuntu ?

So , We can do this by using different tools like `pdftk`,`qpdf` or `pdfseparate`.

- 1 Using `pdftk` (Personally I recommand this )
step 1 :
```
sudo apt install pdftk
```
step 2: 
```
pdftk input_file_name.pdf cat 1-5 7 10-12 output output_file_name_you_want_to_create.pdf
```
Specifying Page Ranges
Extract a Range of Pages
To extract pages 1 through 5:
```
pdftk input.pdf cat 1-5 output output.pdf
```
Extract Specific Pages
To extract only pages 2, 4, and 6:
```
pdftk input.pdf cat 2 4 6 output output.pdf
```
Combine Ranges and Individual Pages
To extract pages 1 through 5, page 7, and pages 10 through 12:
```
pdftk input.pdf cat 1-5 7 10-12 output output.pdf
```
Reverse the Page Order:
To reverse the order of pages 1 through 5:
```
pdftk input.pdf cat 5-1 output output.pdf
```
Extract All Pages :
If you want to copy the entire file (e.g., to test extraction):

```
pdftk input.pdf cat 1-end output output.pdf
````
Examples
Extract the first three pages:
```
pdftk document.pdf cat 1-3 output first_three_pages.pdf
```
Extract non-consecutive pages (e.g., 2, 5, and 8):
```
pdftk document.pdf cat 2 5 8 output selected_pages.pdf
```
_Tips_
If the file name contains spaces, enclose it in quotes:
```
pdftk "my file.pdf" cat 1-3 output "trimmed file.pdf"
```

- 2 Using `qpdf`
Install pdftk:
```
sudo apt install pdftk
```
Extract specific pages:
```
pdftk input.pdf cat 1-5 7 10-12 output output.pdf
```
Replace 1-5 7 10-12 with the range(s) or individual pages you need.

- 3 Using `pdfseparate`
Install poppler-utils:
```
sudo apt install poppler-utils
```
Extract pages: To split the PDF into individual pages:
```
pdfseparate input.pdf page-%d.pdf
```
This creates page-1.pdf, page-2.pdf, etc.
_tips_
Combine the required pages (optional): Use pdfunite (also from poppler-utils) to merge the pages:
```
pdfunite page-1.pdf page-2.pdf output.pdf
```






