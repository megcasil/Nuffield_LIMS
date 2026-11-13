# Nuffield LIMS – Laboratory Information Management System

A web-based Laboratory Information Management System developed using Python and Django to manage biological samples and track their progression through DNA extraction, quality control and sequencing.

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

Install virtual environment.
Install all packages "pip install -r requirements.txt".
Run "python manage.py migrate".
