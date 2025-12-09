# PayMate

This project simulates a banking system and payment gateway to showcase coding skills in four different technologies: Go, Ruby on Rails, Vue.js, and Flutter.

## Components

The project is divided into the following five main components:

1.  **Payment Gateway (Go):** A backend service written in Go that acts as an Acquiring Processor. It accepts payments from e-commerce merchants via a REST API and translates them into ISO 8583 messages to be sent to the Bank for authorization.

2.  **Bank ISO Listener (Go):** A dedicated service written in Go that acts as the Bank's Switch/Interface. It listens for incoming ISO 8583 messages over TCP, parses them, and communicates with the Core Banking API to authorize transactions. It then returns the appropriate ISO 8583 response (e.g., 0210).

3.  **Bank API (Ruby on Rails):** A robust RESTful API built with Rails 8 that serves as the Core Banking System. It manages user accounts, bank accounts, virtual cards, and the general ledger. It exposes internal endpoints for the ISO Listener and public endpoints for the Web/Mobile clients.

4.  **Web Client (Vue.js):** A single-page application (SPA) built with Vue 3. This web interface allows users to interact with the Bank API to manage their accounts, create cards, and view their transaction history.

5.  **Mobile App (Flutter):** A cross-platform mobile application for both Android and iOS, developed using Flutter. It will provide a mobile-native experience for users to access their banking information and perform transactions on the go.

Each component is located in its own dedicated folder within this repository, containing its source code and specific documentation.