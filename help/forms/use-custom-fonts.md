---
title: Use custom fonts 
description: Use custom fonts 
---

# Use custom fonts

**Cloud Service Communications documentation is in beta**

You can use Forms as a Cloud Service Communications to combine an XDP template, XDP-based PDF document, or Acrobat Form (AcroForm) with XML data to generate PDF documents. You can use fonts included in Cloud Service or custom fonts (organization approved fonts) to render the generated PDF documents. You can use the Cloud Service development project to add custom fonts to your Cloud Service environment.

## Behavior of PDF Documents

You can [embed a font](https://adobedocs.github.io/experience-manager-forms-cloud-service-developer-reference/api/sync/#tag/PDFOutputOptions) to a PDF document. When a font is embedded, the PDF document appears (Looks) identical on all platforms. It used embedded font to ensure a consistent look and feel. When a font is not embedded, the font rendering depends on rendering settings of PDF viewer client. If the font is available on the client machine, the PDF uses specified font, else the PDF is rendered with a fallback font.

## Add custom fonts to your Forms as a Cloud Service environment

To add custom fonts to your Cloud Service environment:

1. Setup and open the local development project. You can use any IDE of your choice.
1. At the top-level folder structure of the project, create a folder  to save custom fonts and add custom fonts to the folder. For example, fonts/src/main/resources
![Fonts folder](assets/fonts.png)

1. Open top-level pom.xml file of the development project.
1. Add `<Font-Archive-Version>` manifest entry to the .pom file and set value of version to 1:

    ``` xml

    <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-jar-plugin</artifactId>
        <version>3.1.2</version>
        <configuration>
            <archive>
                <manifest>
                    </addDefaultEntries>
                    </addDefaultImplementationEntries>
                </manifest>
                <manifestEntries>
                    <Font-Archive-Version>1</Font-Archive-Version>
                    <Font-Archive-Contents>/</Font-Archive-Contents>
                </manifestEntries> 
            </archive>
        </configuration>
    </plugin>

    ```

1. Add your fonts folder to `<modules>` listed in the pom file. For example:

    ``` xml

    <modules>
        <module>all</module>
        <module>core</module>
        <module>ui.frontend</module>
        <module>ui.apps</module>
        <module>ui.apps.structure</module>
        <module>ui.config</module>
        <module>ui.content</module>
        <module>it.tests</module>
        <module>dispatcher</module>
        <module>dispatcher.ams</module>
        <module>dispatcher.cloud</module>
        <module>ui.tests</module>
        <module>fonts</module>
    </modules>


    ```

1. Check in the updated code and [run the pipeline](/help/implementing/cloud-manager/deploy-code.md) to deploy the fonts to your Cloud Service environment.
