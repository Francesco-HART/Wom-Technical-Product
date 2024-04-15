# WOM Platform Interaction Diagram

Below is a Mermaid diagram representing the interactions within the WOM platform:

```mermaid
graph TD
    company[("Company\n[Person]")]-.->|Sends to|consumer[("Consumer\n[Person]")]
    consumer-.->|Sends to|company
    company-- "Sign in, create a wallet, check points and rewards" -->womApp[("Wom app\n[Container React - TS]\nWom Dashboard")]
    consumer-- "a user who subscribe to loyalty program" -->womApp
    womApp-- "Create loyalty Program" -->db[("Database\n[Container - SQL]\nWom database")]
    db-- "Read from / write to" -->womApp
    womApp-- "notify by / write to" -->blockchain[("Blockchain\n[Smart contract vetchain]\nWom contracts")]
    womApp-.->|Sends SMS|sms[("SMS\n[Software System]\nAtsuke")]
    womApp-.->|Sends email|email[("Email\n[Software System]\nBrevo")]
    db<-->api[("API\n[Container - NestJS]\nWom API")]
    blockchain<-->api

```

## Description

The diagram illustrates the technical flow of the WOM platform as follows:

- **Company (Person):** Represents a user with a WOM account. This entity interacts with the WOM app to sign in, create a loyalty program, and check customers activities.
- **Consumer (Person):** Represents a user who subscribes to the loyalty program create by a Company. This entity also interacts with the WOM app.
- **Wom App (Container):** The central interface, built with React and TypeScript.
- **Wom API (Container):** The central node in the system, built with NestJs and TypeScript.
- **Database (Container):** A SQL-based container that the WOM app reads from and writes to.
- **Blockchain (Smart contract vetchain):** A blockchain element that interacts with the WOM app through notifications and read/write operations.
- **SMS (Software System):** Represented by Atsuke, it sends SMS messages as part of the platform's operations.
- **Email (Software System):** Represented by Brevo, it sends emails as part of the platform's operations.

All components are styled with specific colors to differentiate between persons, software systems, containers, databases, and blockchain elements.
