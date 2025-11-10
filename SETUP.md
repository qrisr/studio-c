# E-Mail-Formular Setup-Anleitung

Das Kontaktformular auf der Landing Page nutzt **Web3Forms** – ein kostenloser Service, der E-Mails von statischen Websites versendet.

## 🚀 Setup in 3 Schritten:

### Schritt 1: Web3Forms Access Key erhalten

1. Gehe zu: **https://web3forms.com**
2. Klicke auf **"Get Started"** oder **"Create Access Key"**
3. Gib deine E-Mail-Adresse ein: **qris.riner@gmail.com**
4. Bestätige die E-Mail (Check dein Postfach)
5. Kopiere deinen **Access Key** (sieht aus wie: `abc123-def456-ghi789`)

### Schritt 2: Access Key in index.html einfügen

1. Öffne die Datei: `index.html`
2. Suche nach Zeile 953:
   ```html
   <input type="hidden" name="access_key" value="YOUR_ACCESS_KEY_HERE">
   ```
3. Ersetze `YOUR_ACCESS_KEY_HERE` mit deinem echten Access Key:
   ```html
   <input type="hidden" name="access_key" value="abc123-def456-ghi789">
   ```

### Schritt 3: Änderungen commiten und pushen

```bash
git add index.html
git commit -m "Add Web3Forms access key"
git push
```

## ✅ Fertig!

Sobald der Access Key eingefügt ist, funktioniert das Formular:
- Alle Formular-Einreichungen werden an **qris.riner@gmail.com** gesendet
- Du bekommst eine schöne E-Mail mit allen Formular-Daten
- Der Besucher sieht eine Erfolgsmeldung auf der Website

## 📧 Was wird gesendet?

Jede E-Mail enthält:
- **Name** des Kontakts
- **E-Mail-Adresse** des Kontakts
- **Thema** (Workshop-Auswahl)
- **Nachricht** des Kontakts
- **Betreff**: "Neue Kontaktanfrage von KI Workshop Website"

## 🔒 Sicherheit

- Honeypot-Spam-Protection ist bereits aktiviert
- Keine Kreditkarte erforderlich
- Kostenlos bis zu 250 Submissions/Monat
- DSGVO-konform

## 🎨 Features

- ✅ Keine Page-Reloads (AJAX)
- ✅ Erfolgsmeldung wird angezeigt
- ✅ Fehlermeldung bei Problemen
- ✅ Button-Text ändert sich zu "Wird gesendet..."
- ✅ Formular wird nach erfolgreichem Senden geleert

## 🆘 Probleme?

Falls das Formular nicht funktioniert:
1. Überprüfe, ob der Access Key korrekt eingefügt wurde
2. Überprüfe deine E-Mail-Bestätigung bei Web3Forms
3. Schaue in die Browser-Konsole (F12) für Fehler
4. Kontaktiere Web3Forms Support: support@web3forms.com

## Alternative: Formspree

Falls du lieber Formspree nutzen möchtest:
1. Gehe zu https://formspree.io
2. Registriere dich mit qris.riner@gmail.com
3. Erstelle ein neues Formular
4. Ändere die Form-Action zu: `https://formspree.io/f/YOUR_FORM_ID`
