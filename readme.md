Um diese Daten in ihr Image zu bekommen:

- Kopieren die die drei Ordner oder mounten Sie sich den ..\LoadMBils zu ihrem Image

Um das Laden zu starten

- sh M_load_bills.sh im ..\src Verzeichnis aufrufen.
  \*\* Dies erwartet sich ein
  ..\data
  ..\log

- Das Script legt eine Oracle UserID PETROL an.
  (Was optional auf ihren User geändert werden könnte.)

- Das Script legt 4 Tabellen an.

- Das Script fügt via INSERT in zwei Tabellen etwas ein.

- Das Script fügt via SQL\*LOADER in eine Tabelle etwas ein.

Bitte überprüfen Sie alle ..\src Dateien und passen Sie es an ihre Gegebenheit an.

Es könnte sein, dass Teile entfernt wurden :-)

Abschließende führen Sie Queries mit ihren neuen
FACT_BILL und FACT_PETROL Tabellen durch:

Können sie den Trend erkennen, der hier im Vorfeld eingeschleust wurde?

SELECT custname, sum(SUM_BILLAMOUNT) AS SUMMEN FROM FACT_BILL fb
GROUP by custname
ORDER BY 2 DESC;

Mit diesem Query erfahren Sie bei welcher Petrolstation, am meisten Umsatz war.

SELECT PETROLSTATION,
sum(SUM_BILLAMOUNT) AS summe FROM FACT_PETROL fp
GROUP BY PETROLSTATION
ORDER BY 2 DESC;

Durch die kleineren, vorgerechneten Tabellen können Sie sehr schnell ein Ergebnis sehen,
als wenn sie das ganze Query schreiben würden.. siehe script...
