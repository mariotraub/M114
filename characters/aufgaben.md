# Wo wird UTF8 eingesetzt, wo UTF-16?
UTF-8 ist die am weitesten verbreitete Codierung im Internet. Sie wird in:

    HTML/XML-Dokumenten

    E-Mails

    Webservern und APIs

    Linux/Unix-Systemen

    Programmiersprachen (Python, JavaScript, etc.)
    eingesetzt. Der Hauptvorteil ist die Kompatibilität mit ASCII und die Speicherersparnis für lateinische Sprachen.

UTF-16 wird häufig verwendet in:

    Windows-Betriebssystemen

    Java- und .NET-Plattformen (z.B. intern für String-Objekte)

    Einige Formate wie XML in bestimmten Konfigurationen oder Microsoft Office-Dokumente.
# Was bedeutet die Byteorder bei UTF-16?
UTF-16 kann Big Endian (BE) oder Little Endian (LE) sein:

    Das bedeutet, ob das höherwertige Byte oder das niederwertige Byte zuerst gespeichert wird.

    Byte Order Mark (BOM): Ein spezielles Zeichen (0xFEFF), das am Anfang einer Datei stehen kann, um die Reihenfolge anzugeben.

        0xFEFF → Big Endian

        0xFFFE (in umgekehrter Bytefolge gelesen) → Little Endian
# Was bedeutet «abwärtskompatibel» im Zusammenhang mit UTF-8? Existiert diese «Abwärtskompatibilität» auch bei UTF-16?
UTF-8 ist abwärtskompatibel zu ASCII:

    Zeichen von 0–127 (z.B. Buchstaben, Ziffern, Steuerzeichen) sind identisch codiert wie im ASCII-Standard.

    Ein reines ASCII-Dokument ist somit automatisch auch ein gültiges UTF-8-Dokument.

UTF-16 hat keine direkte Abwärtskompatibilität zu ASCII oder anderen Ein-Byte-Zeichensätzen, da jedes Zeichen mindestens 2 Byte lang ist und die Codierung sich unterscheidet.
# Wie beurteilen sie den Speicherbedarf von deutsch- oder englischsprachigem Text bei ISO-8859-Codierung, UTF-8-Codierung und UTF-16-Codierung?
ISO-8859-1 (Latin-1):

    1 Byte pro Zeichen, gut für westliche Sprachen geeignet.

    Keine Unterstützung für z.B. Kyrillisch oder Emoji.

UTF-8:

    Englisch: 1 Byte pro Zeichen (da innerhalb von ASCII).

    Deutsch: Meist 1 Byte (z.B. „a“), aber Umlaute wie „ä“, „ö“, „ü“ und „ß“ benötigen 2 Byte.

    Vorteil: sparsam bei westlichen Sprachen, variabler Speicher.

UTF-16:

    Immer mindestens 2 Byte pro Zeichen.

    Deutsch/Englisch: jedes Zeichen = 2 Byte.

    Vorteil bei asiatischen Sprachen, wo viele Zeichen ohnehin außerhalb der ASCII-Zone liegen.
# Wann wird ein UTF-16-Code vier Byte lang?
Wenn das Zeichen außerhalb der Basic Multilingual Plane (BMP) liegt (also > U+FFFF), z.B. Emoji, Musiksymbole, seltene Schriftzeichen.

Solche Zeichen werden mit Surrogatpaaren codiert:

    Zwei 16-Bit-Werte zusammen = 4 Byte.
# Wie müssen sie vorgehen, wenn sie z.B. in Word ein Zeichen eingeben wollen, das sie auf der Tastatur zwar nicht finden, dessen Unicode sie aber kennen? (z.B. das Eurozeichen)
So gibst du ein Unicode-Zeichen in Microsoft Word ein:

    Tippe den hexadezimalen Unicode-Wert, z. B. 20AC.

    Drücke dann Alt + C.

    Word ersetzt den Code durch das entsprechende Zeichen: €
# Was wird das Problem sein, wenn sie auf dieselbe Weise wie in der vorangegangenen Aufgabedas Unicode-Zeichen des Violinschlüssels (Musiknoten) in eine Wordtext einfügen wollen?
Dieses Zeichen liegt außerhalb der BMP (d.h. es hat einen Wert > U+FFFF).

Probleme:

    Die Word-Methode mit Alt+C funktioniert nur für BMP-Zeichen.

    Für U+1D11E muss man ein geeignetes Symbol einfügen:

        Über das Menü: Einfügen → Symbol → Weitere Symbole → Unicodebereich auswählen

        Oder per Copy & Paste aus einer Unicode-Datenbank oder Webseite.

    Außerdem: Nicht jede Schriftart unterstützt dieses Zeichen (z. B. „Musical Symbols“ muss installiert sein).
