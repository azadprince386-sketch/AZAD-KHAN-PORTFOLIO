# Azad Khan: Personal Skills Portfolio Website
Web Technology (BCS502), Assignment-4, B.Tech CSE Semester V, Greater Noida College of Technology (AKTU).

**Stack:** HTML5, external CSS (Flexbox/Grid, media queries), JavaScript (DOM, fetch), Java 17, Jakarta Servlet 6 (Tomcat 10.1), JDBC, MySQL 8, Maven.

## Folder structure
```
pom.xml                         Maven build (produces portfolio.war)
database/portfolio.sql          creates portfolio_db and contact_messages
src/main/java/.../ContactServlet.java   POST /contact: validate and INSERT
src/main/java/.../DbUtil.java           JDBC connection (reads credentials from env or db.properties)
src/main/resources/db.properties        local DB settings (put your password here)
src/main/webapp/index.html, css/, js/, assets/, WEB-INF/web.xml
report/                         put the printed report here
```

## Run on Windows 11
1. Install JDK 17, Maven 3.9+, MySQL 8 and Apache Tomcat 10.1 (not 9, not 11).
2. Create the database: `mysql -u root -p < database/portfolio.sql`
3. Open `src/main/resources/db.properties` and replace `CHANGE_ME` with your MySQL password
   (or set the environment variables `DB_URL`, `DB_USER`, `DB_PASSWORD`).
4. Build: `mvn clean package` (creates `target/portfolio.war`).
5. Copy `target/portfolio.war` into `<Tomcat>\webapps\`, then run `<Tomcat>\bin\startup.bat`.
6. Open http://localhost:8080/portfolio/ and send a test message.
7. Confirm in MySQL: `SELECT * FROM portfolio_db.contact_messages;`

IntelliJ alternative: open the folder as a Maven project, add a Tomcat 10.1 run configuration, deploy `portfolio:war exploded`.

## Customise
- **Profile photo:** replace `src/main/webapp/assets/azad-profile.jpg` (keep the name; 4:5 portrait works best). A cropped photo from your upload is already there.
- **Project images:** add `project-1.jpg` to `project-5.jpg` in `assets/` and replace each `<div class="ph">` in `index.html` with `<img src="assets/project-1.jpg" alt="...">`.
- **Skill bars:** edit `data-level` (0 to 100) in `index.html`. They are approximate.

## Screenshots to take for the report
Home (dark), Home (light), mobile menu, Skills, Projects, Contact form with a validation error, success message, and the MySQL table after a test submission.

## Submission notes
- Add your **enrolment number** and "Submitted to" on the report cover page (the assignment requires them).
- Last date: 16.11.2026. Source as ZIP or GitHub link, printed report, live demo.
- Testing status: written for the stack above; build and run it on your machine and record your own results.
