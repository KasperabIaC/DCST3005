# Infrastructure as Code (IaC) – Build Once, Deploy Many
Denne oppgaven er basert på koden fra module 07, samt Markdown-videoene 08-02 og 08-03. Oppsettet er hentet ved å kjøre deploy-files-and-folders scriptet. 

1. Lokal utvikling og feature branch
Eneste endringen jeg gjorde lokalt var å legge til en tag for cost-center: IT-Infrastructure. Jeg testet også koden lokalt med terraform init, fmt, validate, og plan for å sjekke at koden faktisk fungerer. 

2. Continuous Integration (CI)
Deretter oprettet jeg en feature branch, feature/add-main-tags, og sender en pull request mot main. Dette utløser CI-pipelinen automatisk. CI er basert på yaml-filen vi har fått, og går igjennom noen enkle sjekker som fmt, validate, plan (kjører plan for alle 3 miljøene). Om alt vises grønt er det tommel opp.

3. Continuous Deployment (CD)
Når pull-requesten er merget til main, vil CD starte. Den deployer til DEV og TEST uten godkjenning, men trenger godkjenning før den kjører PROD. Greit å fikse settings på GitHub først, hvis ikke så kjører den uten godkjenning

4. Deploy til DEV
5. Deploy til TEST
6. Deploy til PROD (med godkjenning)

Sjekket både at endringene skjedde fysisk i Azure, og jeg kjørte også sjekk lokalt med az storage-account show ` --name ... & --resource-group ...

I tillegg opprettet jeg også en versjonering i Github, v1.1.0 - Cost Tracking Tags.

# Oppsummering

Lokal utvikling, skrive og teste kode lokalt på maskinen -> CI, kode validert og planlagt for de 3 miljøene -> Godkjenne pull request og slå sammen feature-branch med main -> CD, deploye til de 3 miljøene, må manuelt godkjenne deploy til dev -> Se at endringer faktisk har blitt gjort i Azure -> Slett ressursene når ferdig 

# Endringer

Det har blitt gjort noen endringer fra opprinnelig oppsett lasted ned med scriptet, blant annet endringer i main.tf, variables.tf og backend.hcl for å passe min infrastruktur i Azure. 