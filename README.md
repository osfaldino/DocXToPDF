# DOCX to PDF Converter

A simple library for converting DOCX documents to PDF format using LibreOffice.

## Prerequisites

1. **LibreOffice**  
   Install the latest version of LibreOffice:  
   [https://www.libreoffice.org/download](https://www.libreoffice.org/download)

2. **.NET 8.0**  
   Ensure that the .NET 8.0 runtime is installed:  
   [https://dotnet.microsoft.com/download](https://dotnet.microsoft.com/download)

## Configuration

Before using the library, configure the parameters in your application code:

```csharp
// Specify the path to the LibreOffice executable
Converter.LibreOfficePath = @"/usr/bin/soffice"; // C:\Program Files\LibreOffice\program\soffice.exe

// Optional: set the timeout in milliseconds (default is 30000 ms)
Converter.TimeOut = 60000;
```

## Usage Example

```csharp
using DocXToPDF;

namespace TestProject1
{
    public class UnitTest
    {
        [Fact]
        public void CreatePdfTest()
        {
            Converter.LibreOfficePath = @"/usr/bin/soffice"; // C:\Program Files\LibreOffice\program\soffice.exe
            Converter.TimeOut = 60000;
            string docxWay = @"FileToBeConverted.docx";
            string pdfWay = @"D:\ConvertedFile.pdf";
            byte[] docxBytes = File.ReadAllBytes(docxWay);
            using (MemoryStream ms = new MemoryStream(docxBytes))
            {
                byte[]? pdfBytes = Converter.ConvertToPdf(ms);
                if (pdfBytes != null)
                    File.WriteAllBytes(pdfWay, pdfBytes);
            }
        }
    }
}
```
