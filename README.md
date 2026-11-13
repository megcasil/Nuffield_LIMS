# LIMS – Laboratory Information Management System

A web-based Laboratory Information Management System developed using Python and Django to manage biological samples and track their progression through DNA extraction, quality control and sequencing.

## Table of Contents

1. [Project Overview](#project-overview)
2. [Key Features](#key-features)
   - [Sample Management](#sample-management)
   - [DNA Extraction Tracking](#dna-extraction-tracking)
   - [Quality Control and Sequencing](#quality-control-and-sequencing)
   - [Automated Taxonomic Information Retrieval](#automated-taxonomic-information-retrieval)
   - [User Interface](#user-interface)
3. [Technologies Used](#technologies-used)
4. [Database Design](#database-design)
5. [Application Architecture](#application-architecture)
6. [Screenshots](#screenshots)
7. [Installation and Setup](#installation-and-setup)
8. [Accessing the Django Admin](#accessing-the-django-admin)
9. [Current Limitations](#current-limitations)
10. [Future Improvements](#future-improvements)
11. [Research Documentation](#research-documentation)
12. [Acknowledgements](#acknowledgements)

## Project Overview

This project was developed as part of a Nuffield Research Placement at the Earlham Institute.

The aim was to design and build a small-scale web-based Laboratory Information Management System (LIMS) to address challenges associated with laboratory data management, sample tracking and data consistency.

The application provides a centralised platform for storing sample information and tracking laboratory workflows, from initial sample registration through to extraction and sequencing.

It also integrates with the National Center for Biotechnology Information (NCBI) database to automatically retrieve taxonomic information, reducing manual data entry and the potential for errors.

## Key Features

### Sample Management
- Register and store biological sample information.
- Record sample names, taxon IDs, scientific names, common names and collection dates.
- Upload and display images associated with individual samples.
- View existing samples through a centralised sample listing.

### DNA Extraction Tracking
- Associate multiple extraction records with individual samples.
- Record extraction dates, names and methods.
- Support predefined extraction methods, including phenol-chloroform, ethanol precipitation and silica.

### Quality Control and Sequencing
- Store quality control information associated with extractions.
- Record quality distribution, ambiguous base content and QC pass/fail status.
- Store sequencing information, including sequencing date, method, mean read length and associated file name.
- View QC and sequencing information through the extraction detail page.

*Note: QC and sequencing records are currently managed through the Django admin interface rather than dedicated user-facing forms.*

### Automated Taxonomic Information Retrieval
- Integrates Biopython with the NCBI database.
- Allows users to enter a taxon ID into the sample form.
- Automatically retrieves the corresponding scientific and common names.
- Uses JavaScript and Django views to populate form fields dynamically.
- Reduces repetitive manual entry and helps improve data consistency.

### User Interface
- Developed using HTML, CSS and JavaScript.
- Uses Bootstrap for responsive styling and a consistent interface.
- Implements reusable Django templates to maintain a consistent layout across application pages.
- Uses Django forms and built-in widgets for data entry and validation.

## Technologies Used

| Technology | Purpose |
|---|---|
| Python 3.11 | Backend development |
| Django 4.2 | Web application framework |
| SQLite | Relational database |
| HTML & CSS | Frontend structure and styling |
| JavaScript | Dynamic form functionality |
| Bootstrap | Responsive user interface |
| Biopython 1.84 | NCBI taxonomic data retrieval |
| NumPy 2.0.1 | Numerical computing dependency |
| Pillow 10.4.0 | Sample image handling |
| Requests 2.32.3 | HTTP requests |

## Database Design

The application uses Django's Object-Relational Mapper (ORM) to manage a relational SQLite database.

Four core models were developed:

- **Sample:** Stores biological sample information and associated images.
- **Extraction:** Stores extraction details and links each extraction to its corresponding sample.
- **QC:** Stores quality control measurements and pass/fail results associated with an extraction.
- **Sequencing:** Stores sequencing information associated with an extraction.

Foreign key relationships connect the models, allowing users to navigate between samples, their extractions and the associated QC and sequencing information.

## Application Architecture

The application follows Django's Model-View-Template (MVT) architecture:

- **Models:** Define the database structure and relationships.
- **Views:** Process HTTP requests, retrieve database records and handle form submissions.
- **Templates:** Render the user interface using reusable HTML templates.
- **Forms:** Handle user input and data validation.
- **URL routing:** Maps application URLs to their corresponding views.

Function-based views were implemented to handle sample creation, sample details, extraction creation and extraction details.

## Screenshots
<img width="944" height="272" alt="image" src="https://github.com/user-attachments/assets/d28741b3-b6e4-4fc1-8b5f-dd0c646b1b18" />
<img width="946" height="412" alt="image" src="https://github.com/user-attachments/assets/d5ac8a08-89c1-4a60-97d0-3af210921f3f" />
<img width="944" height="406" alt="image" src="https://github.com/user-attachments/assets/0da2900a-9f8c-4129-8d81-e323bb5168f2" />
<img width="944" height="437" alt="image" src="https://github.com/user-attachments/assets/b53fbe0c-7c72-4432-b879-51377ef13e03" />
<img width="956" height="437" alt="image" src="https://github.com/user-attachments/assets/46eea729-aa1d-4e82-a42a-d3ce2de056c2" />
<img width="944" height="431" alt="image" src="https://github.com/user-attachments/assets/554da762-26de-43da-9488-d487e82c4313" />

## Installation and Setup

### Prerequisites

- Python 3.11
- pip (Python package installer)
- Git (optional, if cloning the repository rather than downloading the ZIP)

### Setup Instructions

1. Download the project using **Code → Download ZIP** on GitHub and extract the files, or clone the repository using Git.
2. Open a terminal in the main project folder.
3. Create a Python virtual environment using Python 3.11:

```powershell
py -3.11 -m venv .venv
```

4. Activate the virtual environment (Windows PowerShell):

```powershell
.\.venv\Scripts\Activate.ps1
```

5. Install the project dependencies:

```powershell
python -m pip install -r requirements.txt
```

6. Navigate into the Django project directory:

```powershell
cd mysite
```

7. Apply database migrations:

```powershell
python manage.py migrate
```

8. Start the development server:

```powershell
python manage.py runserver
```

9. Open the application in your browser:

**http://127.0.0.1:8000/LIMS/**

## Accessing the Django Admin

The Django administration interface provides access to the management of QC and sequencing records.

To create an administrator account, run the following command from the `mysite` directory:

```powershell
python manage.py createsuperuser
```

Follow the prompts to create your username and password.

Once the development server is running, visit:

**http://127.0.0.1:8000/admin/**

## Current Limitations

- User authentication and role-based access have not yet been implemented for the main application.
- QC and sequencing records can currently only be created through the Django admin interface.
- The application uses SQLite and was developed as a small-scale research project rather than a production laboratory system.
- Custom automated tests have not yet been implemented.

## Future Improvements

The following improvements were identified during development:

- **User authentication:** Introduce login functionality and role-based access to protect sensitive laboratory information.
- **QC and sequencing forms:** Develop dedicated user-facing forms for entering quality control and sequencing data.
- **Automated testing:** Introduce custom automated tests to improve reliability and identify errors during development.
- **Bulk data import:** Enable importing large datasets from Excel spreadsheets to reduce manual data entry.
- **Improved code organisation:** Explore class-based views to improve code reusability and maintainability.
- **Extended taxonomic metadata:** Retrieve additional information, such as taxonomic rank and division, using taxon IDs.
- **External integrations:** Explore synchronisation with other laboratory systems to improve data exchange.

## Research Documentation

The following documents provide further information about the research, development process and project outcomes.

- **[Research Report](docs/LIMS_Research_Report.pdf):** Detailed documentation of the project objectives, methodology, implementation, database design and conclusions.
- **[Research Poster](docs/LIMS_Research_Poster.pdf):** A visual summary of the project's aims, development and key outcomes.

## Acknowledgements

This project was developed as part of a Nuffield Research Placement at the Earlham Institute.

The placement provided an opportunity to explore web application development, database design and the application of software engineering to biological data management.
