RestAPI-TestSample-soapui-project

1. Projekt testuje rzeczywiste, online'owe narzedzie do zarzadzania projektami o nazwie 'Asana' https://www.asana.com/
   W 'Asanie' teamy, pracujace w poszczegolnych 'workspace'ach' tworza projekty i wykonuja w ich obszarze rozne task'i.
   Szczegolowy opis na https://developers.asana.com/docs/object-hierarchy  
   Dokumentacja API dostepna na https://developers.asana.com/docs
   W tym przykladowym projekcie korzystalem glownie z requestow dotyczacych projektow (projects) https://developers.asana.com/docs/projects

2. Opis projektu:
   Projekt wykorzystuje podstawowe metody (CRUD): POST, READ, PUT, DELETE i uzywa autoryzacji OAuth2
   Na poczatku wystepuje request 'Get mutliple workspaces', z ktorego pozyskiwany jest 'workspace ID', uzyty w kolejnych requestach (POST, PUT, READ).

   Projekt ma za zadanie przetestowac mozliwosc utworzenia nowego projektu (project) w danej przestrzeni roboczej (workspace)
   a nastepnie jego edycje i usuniecie. Po kazdej operacji wykonywany jest request 'GET ALL PROJECTS...' ,
   ktory wyswietla aktualna liste projektow w przestrzeni roboczej.

   Dane do kolejnych requestow przypisywane sa ze zmiennych (Properties), przez 'PropertyTransfer' oraz z odpowiedzi 
   poprzednich requestow (response) np. przez GroovyScript.

   Request 'GET ALL PROJECTS after POSTing a new one' zawiera przyklady uzycia roznych asercji, m.in. 'Script Assertion', ktory 
   sprawdza wartosc jednego z wezlow (node) w odpowiedzi (response).

3. Celem tego prostego projektu 'end-to-end' jest zaprezentowanie podstawowych umiejetnosci z zakresu testowania REST API 
   w SoapUI, ktore nabylem korzystajac z online'owych tutoriali. 

4. Zakres wiedzy:
   - Tworzenie Projektu, TestSuite, Test Case, Test Step (PropertyTransfer, Grovy Script)
   - Tworzenie i odwolywanie sie do zmiennych (Properties) na roznych poziomach (Project, Test Suite)
   - Tworzenie prostych Groovy Script'ow. Przekazywanie parametrow pomiedzy requestami/test stepami:
     > Korzystanie z klasy JsonSlurper do parsowania request/response.
     > Korzystanie z klasy JsonBuilder do budowania obiektu JSON'owego. 
     > Korzystanie z klasy testRunner do odwolywania sie do zmiennych na roznych poziomach.
     > Uzycie JsonPath do odwolania sie do wezlow (Node)
   - Korzystnie z 'Property Transfer' do przekazywania parametrow pomiedzy requestami.
   - Tworzenie podstawowych asercji (Contains, Valid/Invalid HTTP Status Codes, ResponseSLA, JsonPath Match/Existence Match/Count, itd.)
   - Tworzenie prostych Script Assertions:
     > Korzystanie z klasy messageExchane do odwolania sie do odpowiedzi (responseContent)
     > Korzystanie z klasy context do odwolania sie do zmiennych na roznych poziomach (np. Test Case)
 
UWAGA! 
Zauwazylem, ze po kazdoraozwym otwarciu SoapUI pojawiaja sie w tym projekcie 2 bledy (pomimo poprawnie zapisanego wczesniej projektu)
1. W requescie 'Delete a project' zmienia sie metoda z DELETE na PUT.
2. Po poprawieniu metody na DELETE, w property transferze o nazwie 'ProjectIDTransfer', (w sekcji Target) zosteje usuniete Property.
   Property powinno byc ustawione na 'project_gid' 
Po poprawieniu tych bledow TestCase dziala poprawnie End-to-End.
      