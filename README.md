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

