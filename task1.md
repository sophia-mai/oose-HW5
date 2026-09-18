1. You are implementing this User Story; what classes will be in your "model" UML class diagram? (Only name the classes.)
   - Professor
   - Student
   - Course
   - Announcement
   - Feed

2. The software system is implemented according to the Client-Server Architecture. To show your understanding of this architecture, describe how the above-stated User Story carries out through the interaction between different entities (user, client, server, database, ...).
   The professor first creates an announcement through the client application. When the professor submits the announcement, the client sends a request containing the annouformation to the sencement information and course inrver. The server receives the request, verifies that the professor has permission to post to the course, and stores the announcement in the database.

   When a student opens or refreshes their feed, the student's client sends a request to the server for the student's feed. The server determines which courses the student belongs to and retrieves the relevant announcements from the database. The server then sends this information back to the client, which displays the professor's announcement on the student's feed.

3. Based on the above-stated User Story (and your general understanding of how a Piazza-like system works), what design pattern(s) [among those we covered in lecture/readings] would be primed for application here. Name only one and elaborate (briefly) on the underlying problem and the proposed solution by the pattern (relate that to how the pattern fits here).
   The Observer pattern would be useful for this system. When a professor posts a new announcement for a course, multiple students associated with that course get the new announcement. Directly having the professor or announcement manage every individual student would create unnecessary coupling.

   Using the Observer pattern, students can act as observers/subscribers of a course, while the course can act as the subject/publisher. When a professor posts a new announcement to the course, the subject can notify its subscribed students that new content is available. This allows students to receive updates without the announcement-posting logic needing to know the details of every individual student.

   This also keeps the system loosely coupled because new students can subscribe to a course or leave a course without changing the announcement-posting behavior.
