<html lang="pt-BR">
<head>
<meta charset="utf-8"/>
<meta content="width=device-width, initial-scale=1.0" name="viewport"/>
<title>Gerenciador de Notas de Boletim - APP</title>
<style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; /* Modern font */
            margin: 0;
            background-color: #F5DEB3; /* Light brown background color (Wheat) */
            color: #A52A2A; /* Primary color */
            min-height: 100vh;
            padding-bottom: 40px; /* Add bottom padding for fixed footer */
            box-sizing: border-box; /* Include padding in total height */
        }
        /* Center login container when visible */
        body:has(#loginContainer:not(.hidden)) {
            display: flex;
            justify-content: center;
            align-items: center;
            background: linear-gradient(to bottom right, #8B4513, #654321); /* Brown gradient background for login */
            padding-bottom: 0; /* Remove body padding on login screen */
        }

        h1, h2, h3 {
            color: #A52A2A; /* Primary color */
        }
        h2, h3 {
            border-bottom: 2px solid yellow; /* Accent color for borders */
            padding-bottom: 5px;
        }
        table {
            width: 100%; /* Ensure tables take full available width */
            border-collapse: collapse;
            margin-top: 20px;
        }
        th, td {
            border: 1px solid yellow; /* Border color for table cells */
            padding: 8px;
            text-align: center;
        }
        th {
            background-color: #A52A2A; /* Primary color for table headers */
            color: white;
        }
        tr:hover:not(.student-group-header):not(.no-hover) { /* Added hover for table rows */
            background-color: #f9f9f9; /* Lighter background on hover */
            cursor: pointer;
        }
        .button {
            background-color: yellow; /* Accent color for buttons */
            color: #8B4513; /* Brown text for buttons */
            padding: 10px 15px;
            border: none;
            cursor: pointer;
            margin: 5px;
            border-radius: 5px;
            display: block;
            width: calc(100% - 10px);
            transition: background-color 0.3s ease, transform 0.2s ease, box-shadow 0.2s ease; /* Smooth transition for all effects */
        }
        .button:hover {
            background-color: #f0c000; /* Lighter yellow on hover */
            transform: translateY(-2px); /* Subtle lift effect */
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15); /* Add shadow on hover */
        }
        .button:active {
            transform: translateY(0); /* Return to original position on click */
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); /* Smaller shadow on active */
        }
         .button:disabled {
            background-color: #ccc;
            cursor: not-allowed;
            transform: none; /* No transform when disabled */
            box-shadow: none; /* No shadow when disabled */
        }
         .button.delete-button {
             background-color: #dc3545; /* Red for delete button */
         }
         .button.delete-button:hover {
             background-color: #c82333; /* Lighter red on hover */
          }
        .hidden {
            display: none !important;
        }
        .error {
            color: #dc3545; /* Error message color */
            font-size: 14px;
            margin-top: 10px; /* Space above */
        }

        /* --- Improved Login Screen Styles --- */
        #loginContainer {
            text-align: center;
            padding: 50px 45px; /* Increased padding for larger feel */
            border: none; /* Remove border */
            border-radius: 10px; /* More rounded corners */
            background-color: #ffffff; /* White background */
            position: relative;
            overflow: hidden;
            width: 90%; /* Increased width */
            max-width: 800px; /* Increased max-width for login container */
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.15); /* More pronounced shadow */
        }
        /* Highlighted School Name */
        #loginContainer .senac-title {
            font-size: 3.5em; /* Larger size */
            font-weight: bold;
            color: #8B4513; /* Brown accent color */
            margin-bottom: 40px; /* More space below */
            line-height: 1.1;
        }

        /* Login Watermark Logo (Adjusted) */
        .login-watermark {
            position: absolute;
            bottom: 10px; /* Bottom position */
            left: 50%;
            transform: translateX(-50%);
            opacity: 0.05; /* More subtle */
            z-index: 0;
            pointer-events: none;
            width: 70%; /* Relative width */
        }
        .login-watermark img {
             max-width: 100%;
             height: auto;
        }

        /* Improved Input Fields */
        #loginContainer input[type="text"],
        #loginContainer input[type="password"] {
            padding: 18px; /* More internal padding */
            margin: 18px 0; /* More vertical space */
            width: 100%;
            border-radius: 5px;
            border: 1px solid yellow; /* Subtle border */
            box-sizing: border-box;
            font-size: 18px; /* Larger font size */
            transition: border-color 0.3s ease, box-shadow 0.3s ease; /* Transitions */
        }
        #loginContainer input[type="text"]:focus,
        #loginContainer input[type="password"]:focus {
            border-color: #A52A2A; /* Primary color on focus */
            box-shadow: 0 0 0 3px rgba(165, 42, 42, 0.2); /* Outer shadow on focus using primary color */
            outline: none; /* Remove default outline */
        }

         /* Improved Login Button */
         #loginContainer #loginButton {
             width: 100% !important; /* Full width */
             display: block !important;
             padding: 20px 35px; /* Generous padding */
             margin-top: 30px; /* Space above */
             font-size: 20px; /* Larger Font size */
             font-weight: bold;
             background-color: yellow; /* Accent color */
             border: none;
             border-radius: 5px;
             color: #8B4513; /* Brown text */
             cursor: pointer;
             transition: background-color 0.3s ease, box-shadow 0.3s ease, transform 0.2s ease; /* Added transform transition */
         }
         #loginContainer #loginButton:hover {
             background-color: #f0c000; /* Lighter yellow on hover */
             box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
             transform: translateY(-2px); /* Lift effect on hover */
         }
         #loginContainer #loginButton:active {
             transform: translateY(0); /* Pressed effect on click */
             box-shadow: 0 1px 3px rgba(0, 0, 0, 0.2);
         }
         /* --- End Login Styles --- */


        #appContainer {
            display: flex;
            width: 100%;
            height: 100vh;
            overflow: hidden;
            background-color: #F5DEB3; /* Changed to light brown */
        }

        #sidebar {
            width: 220px; /* Slightly narrower sidebar for more content space */
            background-color: white; /* Sidebar background color */
            padding: 20px; /* Increased padding */
            display: flex;
            flex-direction: column;
            border-right: 1px solid yellow; /* Sidebar border */
            height: 100%;
            box-sizing: border-box;
            flex-shrink: 0;
        }
        #sidebar h2, #sidebar h3 {
            margin-top: 15px; /* More margin */
            margin-bottom: 15px;
            font-size: 1.2em; /* Adjusted size */
            color: #A52A2A; /* Darker text color */
        }
        #sidebar .button {
            margin-bottom: 12px; /* Increased margin */
             text-align: left; /* Align button text */
             padding: 12px 15px; /* Increased padding */
             width: 100%; /* Full width */
             box-sizing: border-box;
        }
        #sidebar .button.logout-button {
            margin-top: auto;
            background-color: yellow; /* Logout button color */
            color: #8B4513; /* Brown text */
        }
         #sidebar .button.logout-button:hover {
             background-color: #f0c000; /* Lighter yellow on hover */
         }

        #mainContentArea {
            flex-grow: 1;
            padding: 30px 5px; /* Reduced horizontal padding for more table width */
            overflow-y: auto;
            height: calc(100vh - 40px); /* Adjust height for footer */
            box-sizing: border-box;
            position: relative;
        }
        /* App Text - Top Right Corner */
        #appHeaderText {
            position: fixed;
            top: 20px; /* Adjusted position */
            right: 30px; /* Adjusted position */
            font-size: 2.2em; /* Large size */
            font-weight: bold;
            color: yellow; /* Accent color */
            z-index: 1001;
        }


        #mainContentArea h1 {
            margin-top: 0;
            margin-bottom: 30px; /* More space below main title */
        }

        /* General adjustments for inputs/selects within the App */
        input[type="text"], input[type="password"], select, textarea { /* Added textarea */
            padding: 12px; /* Increase padding */
            margin: 8px 5px; /* Adjust margin */
            width: auto; /* Allow initial auto adjustment */
            min-width: 200px; /* Minimum width */
            border-radius: 5px;
            border: 1px solid yellow; /* Border color */
            box-sizing: border-box;
            font-size: 16px; /* Increased font size */
            transition: border-color 0.3s ease, box-shadow 0.3s ease; /* Transitions */
        }
         input[type="text"]:focus, select:focus, textarea:focus { /* Added textarea focus */
            border-color: #A52A2A; /* Primary color on focus */
            box-shadow: 0 0 0 3px rgba(165, 42, 42, 0.2); /* Outer shadow on focus */
            outline: none; /* Remove default outline */
         }
         input[type="text"]:disabled, select:disabled {
             background-color: white; /* Disabled background */
             cursor: not-allowed;
         }
        /* Inline buttons with inputs */
        #addStudentSection button, #addDisciplineSection button, #mainContentArea h2 + button, #mainContentArea h3 + button,
        #printControls button /* Style for new print buttons */
         {
             width: auto !important;
             display: inline-block !important;
             vertical-align: middle; /* Align with selects/inputs */
             margin-left: 10px;
        }
        /* Adjustment for observation input, can be wider */
        #addDisciplineSection input[type="text"]#observationInput {
            min-width: 300px; /* Allow a bit more space for observation */
        }
         /* Style for the non-editable 'Média' display */
        #mediaDisplay {
            margin-top: 10px;
            font-weight: bold;
            color: #A52A2A;
            padding: 10px;
            border: 1px solid yellow;
            border-radius: 5px;
            background-color: white;
            display: inline-block; /* Aligns well with other form elements */
            min-width: 120px;
            text-align: center;
        }


        /* Modal styles */
        .modal {
            position: fixed;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.5);
            z-index: 1000;
            display: flex;
            justify-content: center;
            align-items: center;
            animation: fadeIn 0.3s ease-out; /* Fade in animation for modal */
        }
        .modal-content {
            background-color: white;
            padding: 30px; /* Increased padding */
            border-radius: 8px;
            width: 90%; /* Responsive width */
            max-width: 1100px; /* Increased max-width for modals */
            max-height: 90vh; /* Max height to fit within viewport */
            overflow-y: auto;
            position: relative;
            z-index: 1002;
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.25); /* Stronger shadow for modals */
            animation: slideInFromTop 0.3s ease-out; /* Slide in animation for modal content */
        }
        .modal-content h2 { margin-top: 0; }
        .modal-content label{ display: block; margin-top: 15px; font-weight: bold; } /* Increased margin */
        .modal-content input[type="text"], .modal-content input[type="password"], .modal-content select { width: 100%; padding: 12px; font-size: 1em; } /* Inputs in modal 100% and larger */
        .close-button { position: absolute; top: 15px; right: 20px; font-size: 28px; font-weight: bold; cursor: pointer; color: #A52A2A; transition: color 0.2s ease, transform 0.2s ease; } /* Larger close button */
        .close-button:hover {
            color: #dc3545; /* Red on hover */
            transform: rotate(90deg); /* Spin effect */
        }
        #professorDisciplinesCheckboxes div, #professorClassesCheckboxes div, #editProfessorDisciplinesCheckboxes div, #editProfessorClassesCheckboxes div { margin-bottom: 8px; } /* Increased margin */
        #professorDisciplinesCheckboxes label, #professorClassesCheckboxes label, #editProfessorDisciplinesCheckboxes label, #editProfessorClassesCheckboxes label { margin-left: 8px; font-weight: normal; display: inline-block; margin-right: 15px; font-size: 1.05em; } /* Increased font size */
        #professorDisciplinesCheckboxes input[type="checkbox"], #professorClassesCheckboxes input[type="checkbox"], #editProfessorDisciplinesCheckboxes input[type="checkbox"], #editProfessorClassesCheckboxes input[type="checkbox"] { vertical-align: middle; transform: scale(1.1); } /* Slightly larger checkboxes */

         /* Specific styles for discipline/class assignment checkboxes */
        .discipline-assignment {
            margin-bottom: 20px; /* More space */
            padding: 15px; /* More padding */
            border: 1px solid yellow; /* Border for assignment box */
            border-radius: 8px; /* More rounded */
            background-color: white; /* Background for assignment box */
            transition: background-color 0.3s ease;
        }
        .discipline-assignment:hover {
            background-color: #fffacd; /* Light yellow on hover */
        }
        .discipline-assignment h4 {
            margin-top: 0;
            margin-bottom: 10px; /* More space */
            color: #A52A2A; /* Text color */
            font-size: 1.2em; /* Larger font */
        }
        .discipline-assignment .class-checkboxes label {
            margin-right: 20px; /* More spacing */
             font-weight: normal;
        }


        /* Style for editable cells */
        .editable-cell {
            cursor: pointer;
            border: 1px dashed yellow; /* Dashed border to indicate editable */
            padding: 5px; /* Add some padding */
            transition: background-color 0.2s ease; /* Smooth transition for hover */
        }
         .editable-cell:hover {
             background-color: #fffacd; /* Highlight on hover (light yellow) */
         }
         .editable-cell.editing {
             background-color: #fff; /* White background when editing */
         }
         .editable-cell input[type="text"], .editable-cell select {
             width: calc(100% - 2px); /* Account for borders */
             padding: 4px;
             margin: 0;
             border: 1px solid #ccc; /* Visible border when editing */
             background: #f9f9f9; /* Light background when editing */
             text-align: center;
             font-size: inherit;
             font-family: inherit;
             box-sizing: border-box;
             outline: none; /* Remove outline when editing */
             transition: border-color 0.3s ease, box-shadow 0.3s ease; /* Transitions */
         }
         .editable-cell input[type="text"]:focus, .editable-cell select:focus {
             border-color: #A52A2A; /* Primary color on focus */
             box-shadow: 0 0 0 2px rgba(165, 42, 42, 0.2); /* Smaller shadow for inline edits */
         }


        /* Styles for User Management Table */
        #manageUsersSection table {
             margin-top: 15px;
             width: 100%;
        }
         #manageUsersSection table th, #manageUsersSection table td {
             text-align: left;
              padding: 12px; /* More padding */
         }
          #manageUsersSection table td:nth-last-child(3) { /* Disciplines Assigned Column (third to last before Actions) */
             font-size: 0.95em;
             overflow-wrap: break-word; /* Break text if too long */
          }
           #manageUsersSection table td:nth-last-child(2) { /* Classes Assigned Column (second to last before Actions) */
             font-size: 0.95em;
             overflow-wrap: break-word; /* Break text if too long */
          }
           #manageUsersSection table th:nth-last-child(3), #manageUsersSection table td:nth-last-child(3) {
              text-align: center; /* Center Disciplines title and content */
           }
           #manageUsersSection table th:nth-last-child(2), #manageUsersSection table td:nth-last-child(2) {
              text-align: center; /* Center Classes title and content */
           }
          #manageUsersSection table td:nth-last-child(1) { /* Password Column */
             font-family: 'Courier New', Courier, monospace; /* Monospaced font for passwords */
             font-size: 0.95em;
             overflow-wrap: break-word; /* Break password if too long */
          }
          #manageUsersSection table th:nth-last-child(1), #manageUsersSection table td:nth-last-child(1) { /* Center Password title */
             text-align: center;
          }
           #manageUsersSection table td:last-child { /* Actions Column */
                text-align: center;
                width: 140px; /* More space for buttons */
           }
           #manageUsersSection table .button {
                width: auto;
                display: inline-block;
                margin: 4px; /* More margin */
           }
            #manageUsersSection p { /* Message when no users */
                 text-align: center;
                 font-style: italic;
                 color: #A52A2A; /* Text color */
                 font-size: 1.1em;
            }
            #manageUsersSection .security-warning {
                color: #dc3545; /* Warning color */
                text-align: center;
                margin-top: 25px; /* More margin */
                font-weight: bold;
                font-size: 1.1em;
            }

            /* Styles for Professor Section */
             #professorSection h1 {
                 margin-bottom: 20px; /* More margin */
             }
             #professorSection p {
                 margin-bottom: 20px;
                 font-size: 1.1em;
             }
              #professorSection label {
                  font-weight: bold;
                  margin-right: 8px; /* More margin */
                  font-size: 1.1em;
              }
              #professorSection select {
                 margin-right: 20px; /* More margin */
                 padding: 10px; /* Larger padding */
                 font-size: 1.05em;
              }
              #professorSection table.professor-table th, #professorSection table.professor-table td {
                   text-align: center; /* Center cells in professor table */
                   padding: 10px; /* Larger padding */
               }
               #professorSection table.professor-table td:first-child {
                  text-align: left; /* Student name aligned left */
               }
                /* Adjustment for observation cell in professor table */
               #professorSection table.professor-table td:last-child {
                   text-align: left; /* Align observations left */
               }

            /* Fixed footer in the application */
            #appFooter {
                width: 100%;
                height: 50px; /* Larger Footer height */
                background-color: #dc3545; /* Primary color for footer */
                color: white;
                text-align: center;
                line-height: 50px; /* Vertically center text */
                font-size: 1em; /* Slightly larger font */
                position: fixed; /* Fix to bottom */
                bottom: 0;
                left: 0;
                z-index: 1000;
            }

            /* Styles for Print Options in Student Bulletin Section */
            #studentPrintOptions {
                margin-bottom: 25px; /* More margin */
                padding: 20px; /* More padding */
                border: 1px solid yellow; /* Border color */
                border-radius: 8px; /* More rounded */
                background-color: white; /* Background color */
            }
            #studentPrintOptions label {
                display: inline-block;
                margin-right: 20px; /* More margin */
                font-weight: normal;
                font-size: 1.05em;
            }
            #studentPrintOptions input[type="checkbox"],
            #studentPrintOptions input[type="radio"] {
                margin-right: 8px; /* More margin */
                vertical-align: middle;
                transform: scale(1.1); /* Slightly larger */
            }


        /* Print Styles (UPDATED) */
        @media print {
            body { margin: 0; display: block; background-color: #fff !important; color: #A52A2A !important; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; font-size: 10pt; }
            body:has(#loginContainer:not(.hidden)) { display: none !important; } /* Hide everything if on login screen */
             body { padding-bottom: 0 !important; } /* Remove body bottom padding on print */


            /* Hide UI elements */
            #sidebar, #loginContainer, .modal, .button, input, select,
             .unitCheckbox, .studentUnitCheckboxPrint, /* Hide all unit checkboxes */
             label[for="studentSelectPrint"], label[for="reportType"], label.admin-print-label, /* Hide admin print specific labels */
             #searchName, .close-button, th button, td button, #appHeaderText, .login-watermark,
             #loginContainer .senac-title, #manageUsersSection, #manageUsersSection table .button, #manageUsersSection .security-warning,
             #professorSection select, #professorSection label, #appFooter,
             #studentBulletinSection .button, /* Hide print button in student bulletin on print */
             #studentPrintOptions /* Hide the student's print options container */,
             #professorNotesSection .button, #professorNotesSection label, #professorNotesSection select, #professorNotesSection textarea,
             #professorNotesSection h3 /* Hide professor notes controls on print */
            { display: none !important; }

             #appContainer{ display: block; height: auto; width: 100%; overflow: visible; background-color: #fff !important;}
             #mainContentArea { width: 100%; padding: 0; overflow-y: visible; height: auto; flex-grow: 0; }

             /* Table Styles for Print */
             table { width: 100%; border-collapse: collapse; margin-top: 10px; }
             th, td { border: 1px solid #A52A2A !important; padding: 6px; text-align: center; font-size: 9pt; }
             th { background-color: yellow !important; color: #A52A2A !important; font-weight: bold; }
             td { text-align: center; } /* Ensure data cells are centered */
             td:first-child { text-align: left; } /* Align student name left in table */
             /* Adjustment for the new Observations column in print */
             #studentTable td:nth-last-child(2), #professorStudentTable td:nth-last-child(1) {
                 text-align: left; /* Align observation text left */
                 font-size: 8pt; /* Slightly smaller font if observation is long */
             }


             /* Control page breaks */
             tr { page-break-inside: avoid; page-break-after: auto; }
             table, tr, td, th { page-break-inside: avoid !important; } /* Prevent breaks inside table elements */
              .student-report { page-break-inside: avoid; page-break-after: always; margin-bottom: 0; padding: 10px 0;} /* Ensure report block stays together and force break after */
              .student-report:last-child { page-break-after: avoid; margin-bottom: 0; } /* Don't force break after the last report */

             /* Styles for each report header */
              .student-report div:first-child { text-align: center; margin-bottom: 10px; padding-bottom: 5px; border-bottom: 1px solid yellow;}
              .student-report h2 { color: #A52A2A !important; border-bottom: none; margin: 0; padding: 0; font-size: 14pt;}
              .student-report p { margin: 2px 0; font-size: 10pt;}
              .student-report strong { font-weight: bold; }

             /* Styles for the generated bulletin table */
             .bulletin-table {
                 width: 100%;
                 border-collapse: collapse;
                 margin-top: 15px;
             }
             .bulletin-table th, .bulletin-table td {
                 border: 1px solid #A52A2A !important;
                 padding: 8px;
                 text-align: center;
                 font-size: 9pt;
             }
             .bulletin-table th {
                 background-color: yellow !important; /* Light background for bulletin header */
                 color: #A52A2A !important;
                 font-weight: bold;
             }
             .bulletin-table td {
                  text-align: center;
             }
             .bulletin-table td:first-child {
                 text-align: left; /* Discipline name aligned left */
             }
              .bulletin-table td:last-child {
                  text-align: left; /* Observation aligned left */
              }

             /* New styles for the bulletin header layout */
              .bulletin-header {
                  text-align: center;
                  margin-bottom: 20px; /* More space below the header block */
                  padding-bottom: 15px; /* More padding below the header content */
                  border-bottom: 2px solid #A52A2A !important; /* Thicker border */
              }
              .bulletin-header h2 {
                  margin-top: 0;
                  margin-bottom: 5px; /* Space below the main title */
                  font-size: 16pt; /* Slightly larger font */
                  color: #A52A2A !important; /* Ensure black color for printing */
              }
               .bulletin-header p {
                   margin: 5px 0; /* More space between paragraphs */
                   font-size: 11pt; /* Slightly larger font for student info */
                   color: #A52A2A; /* Ensure dark color */
               }
               .bulletin-header p strong {
                   font-weight: bold;
               }
                /* Specific styles for the consolidated header lines */
                .bulletin-header .line1 {
                    font-size: 18pt; /* Larger font for the main title line */
                    font-weight: bold;
                    margin-bottom: 8px; /* Space below line 1 */
                }
                 .bulletin-header .line2 {
                     font-size: 14pt; /* Slightly smaller for the secondary title */
                     margin-bottom: 8px; /* Space below line 2 */
                 }
                  .bulletin-header .line3 {
                      font-size: 11pt; /* Standard font for student info line */
                      margin-top: 8px; /* Add space above line 3 */
                      margin-bottom: 0; /* No margin below the last line of the header block */
                  }


             /* Page Margins */
              @page { size: A4; margin: 1.5cm; } /* Define page margins */
              body { padding: 0; } /* Remove body padding if margin is defined in @page */

              /* Ensure editable cell content is printed */
             .editable-cell span { display: inline !important; }

             /* New styles for professor notes section for print */
             .professor-notes-print {
                 margin-top: 25px;
                 padding-top: 15px;
                 border-top: 1px solid yellow; /* Border color */
             }
             .professor-notes-print h4 {
                 font-size: 12pt;
                 margin-bottom: 10px;
                 color: #A52A2A !important; /* Text color */
             }
             .professor-note-item {
                 border: 1px solid yellow; /* Border color */
                 padding: 8px;
                 margin-bottom: 8px;
                 background-color: white; /* Background color */
             }
             .professor-note-item p {
                 margin: 0;
                 line-height: 1.4;
             }
             .professor-note-item strong {
                 font-weight: bold;
             }
             .professor-note-item span {
                 font-size: 9pt;
                 color: #A52A2A; /* Text color */
                 display: block;
                 margin-top: 5px;
             }


        }
         /* Styling for grouped student rows */
         .student-group-header td {
             background-color: white; /* Light background for student header */
             font-weight: bold;
             text-align: left !important; /* Align student info left */
         }
          .student-group-header td:first-child {
              border-left: 3px solid #A52A2A; /* Primary color left border */
          }

         .discipline-row td {
             border-top: none; /* Remove top border for discipline rows */
         }
         .discipline-row td:first-child {
             padding-left: 30px; /* Indent discipline name */
             text-align: left !important; /* Align discipline name left */
         }
          /* Adjust padding for other cells in discipline rows if needed */
          .discipline-row td:not(:first-child) {
              text-align: center; /* Center other cells */
          }
           .discipline-row td:last-child {
              text-align: center; /* Center actions cell */
           }

        /* Styles for Professor Notes Section */
        #professorNotesSection {
            margin-top: 30px;
            padding: 20px;
            border: 1px solid yellow; /* Border color */
            border-radius: 8px;
            background-color: white; /* Background color */
        }
        #professorNotesSection h3 {
            border-bottom: 2px solid #A52A2A; /* Primary color for border */
            margin-bottom: 15px;
        }
        #professorNotesSection .note-controls label {
            margin-right: 5px;
            font-weight: bold;
        }
        #professorNotesSection .note-controls select {
            margin-right: 15px;
        }
        #professorNotesSection textarea {
            width: 100%;
            min-height: 100px;
            padding: 10px;
            margin-top: 15px;
            border: 1px solid yellow; /* Border color */
            border-radius: 5px;
            box-sizing: border-box;
            font-size: 1em;
            resize: vertical;
        }
        #professorNotesSection .note-display {
            margin-top: 25px;
            border-top: 1px solid yellow; /* Border color */
            padding-top: 15px;
        }
        .professor-note-item {
            border: 1px solid yellow; /* Border color */
            background-color: white; /* Background color */
            padding: 12px;
            margin-bottom: 10px;
            border-radius: 6px;
            position: relative;
        }
        .professor-note-item p {
            margin: 0 0 5px 0;
            line-height: 1.4;
        }
        .professor-note-item strong {
            color: #A52A2A; /* Primary color */
        }
        .professor-note-item span.note-meta {
            display: block;
            font-size: 0.85em;
            color: #A52A2A; /* Text color */
            margin-top: 8px;
            border-top: 1px solid yellow; /* Border color */
            padding-top: 5px;
        }
        .professor-note-item .delete-note-button {
            position: absolute;
            top: 10px;
            right: 10px;
            background-color: #dc3545; /* Delete button color */
            color: white;
            border: none;
            border-radius: 4px;
            padding: 4px 8px;
            font-size: 0.75em;
            cursor: pointer;
            transition: background-color 0.2s ease;
        }
        .professor-note-item .delete-note-button:hover {
            background-color: #c82333; /* Lighter color on hover */
        }
        #studentProfessorNotes {
            margin-top: 30px;
            padding: 20px;
            border: 1px solid yellow; /* Light border color */
            border-radius: 8px;
            background-color: white; /* Light background color */
        }
        #studentProfessorNotes h2 {
            border-bottom: 2px solid #dc3545; /* Accent color for border */
            color: #A52A2A; /* Darker text color */
            margin-bottom: 20px;
        }
        #studentProfessorNotes .no-notes {
            text-align: center;
            font-style: italic;
            color: #A52A2A; /* Text color */
        }
        /* Keyframe animations */
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        @keyframes slideInFromTop {
            from { transform: translateY(-50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }
</style>
</head>
<body>
<div id="loginContainer">
<div class="login-watermark">
<img alt="Logo Escola Academia Primeiros Passos" src="senac_logo.png"/>
</div>
<h1 class="senac-title">Escola Academia Primeiros Passos</h1>
<p style="color: #8B4513; margin-top: -20px; margin-bottom: 20px; font-size: 1.2em;">Boletim Escolar - APP</p> <input id="username" placeholder="Usuário" type="text"/>
<input id="password" placeholder="Senha" type="password"/>
<button class="button" id="loginButton" type="button">Entrar</button>
<p class="error" id="loginError"></p>
</div>
<div class="hidden" id="appContainer">
<div id="sidebar">
<button class="button" onclick="goHome()" type="button">Voltar ao Início</button>
<div class="hidden" id="userManagementSection">
<h3>Gerenciar Usuários</h3>
<button class="button" onclick="showAddProfessorForm()" type="button">Adicionar Professor</button>
<button class="button" onclick="showAddCoordenadorForm()" type="button">Adicionar Coordenador</button>
<button class="button" onclick="showManageUsersSection()" type="button">Gerenciar Professores/Coordenadores</button><button class="button" onclick="showAddAlunoUserForm()" type="button">Adicionar Usuário de Aluno</button>
</div>
<button class="button hidden" id="professorAgendaButton" onclick="showProfessorNotesSection()" type="button">Agenda do Professor</button>
<hr class="hidden" id="sidebarHr"/>
<button class="button logout-button" onclick="logout()" type="button">Sair</button>
</div>
<div id="mainContentArea">
<div id="appHeaderText">APP</div>
<div class="hidden" id="studentBulletinSection">
    <h1>Meu Boletim</h1>
    <div id="studentPrintOptions">
        <h3>Opções de Impressão:</h3>
        <div>
            <label class="admin-print-label">Selecione as Unidades:</label>
            <div>
                <label><input class="studentUnitCheckboxPrint" type="checkbox" value="1" checked/> Unidade 1</label>
                <label><input class="studentUnitCheckboxPrint" type="checkbox" value="2" checked/> Unidade 2</label>
                <label><input class="studentUnitCheckboxPrint" type="checkbox" value="3" checked/> Unidade 3</label>
                <label><input class="studentUnitCheckboxPrint" type="checkbox" value="4" checked/> Unidade 4</label>
            </div>
        </div>
        <div style="margin-top: 10px;">
            <label class="admin-print-label"><input name="studentReportType" type="radio" value="full" checked/> Incluir Avaliações</label>
            <label class="admin-print-label"><input name="studentReportType" type="radio" value="summary"/> Somente Menção e Situação</label>
        </div>
    </div>
    <button class="button" onclick="printMyBulletin()" type="button" style="width: auto; margin-bottom: 20px;">Imprimir Meu Boletim</button>
    <div id="studentBulletinContent">
        <p style="text-align: center; font-style: italic;">Carregando boletim...</p>
    </div>
    <div id="studentProfessorNotes">
        <h2>Anotações dos Professores</h2>
        <div id="studentNotesContent">
            <p class="no-notes">Nenhuma anotação disponível.</p>
        </div>
    </div>
</div>

<div class="hidden" id="studentManagementSection"> <h1>Gerenciador de Notas de Boletim</h1>
<div class="hidden" id="addStudentSection">
    <h2>Adicionar Aluno</h2>
    <div>
        <label for="studentName">Nome do Aluno:</label>
        <input id="studentName" placeholder="Nome completo do aluno" type="text"/>
    </div>
    <div>
        <label for="studentMatricula">Matrícula:</label>
        <input id="studentMatricula" placeholder="Matrícula do aluno" type="text"/>
    </div>
    <div>
        <label for="class">Turma:</label>
        <select id="class">
            <option value="">Selecione a Turma</option>
            <optgroup label="Educação Infantil">
                <option value="ED. Infantil 1 Turma A">ED. Infantil 1 Turma A</option>
                <option value="ED. Infantil 1 Turma B">ED. Infantil 1 Turma B</option>
                <option value="ED. Infantil 1 Turma C">ED. Infantil 1 Turma C</option>
                <option value="ED. Infantil 1 Turma D">ED. Infantil 1 Turma D</option>
                <option value="ED. Infantil 2 Turma A">ED. Infantil 2 Turma A</option>
                <option value="ED. Infantil 2 Turma B">ED. Infantil 2 Turma B</option>
                <option value="ED. Infantil 2 Turma C">ED. Infantil 2 Turma C</option>
                <option value="ED. Infantil 2 Turma D">ED. Infantil 2 Turma D</option>
                <option value="ED. Infantil 3 Turma A">ED. Infantil 3 Turma A</option>
                <option value="ED. Infantil 3 Turma B">ED. Infantil 3 Turma B</option>
                <option value="ED. Infantil 3 Turma C">ED. Infantil 3 Turma C</option>
                <option value="ED. Infantil 3 Turma D">ED. Infantil 3 Turma D</option>
            </optgroup>
            <optgroup label="Fundamental 1">
                <option value="1 ANO A Fundamental 1">1 ANO A Fundamental 1</option>
                <option value="1 ANO B Fundamental 1">1 ANO B Fundamental 1</option>
                <option value="1 ANO C Fundamental 1">1 ANO C Fundamental 1</option>
                <option value="1 ANO D Fundamental 1">1 ANO D Fundamental 1</option>
                <option value="2 ANO A Fundamental 1">2 ANO A Fundamental 1</option>
                <option value="2 ANO B Fundamental 1">2 ANO B Fundamental 1</option>
                <option value="2 ANO C Fundamental 1">2 ANO C Fundamental 1</option>
                <option value="2 ANO D Fundamental 1">2 ANO D Fundamental 1</option>
                <option value="3 ANO A Fundamental 1">3 ANO A Fundamental 1</option>
                <option value="3 ANO B Fundamental 1">3 ANO B Fundamental 1</option>
                <option value="3 ANO C Fundamental 1">3 ANO C Fundamental 1</option>
                <option value="3 ANO D Fundamental 1">3 ANO D Fundamental 1</option>
                <option value="4 ANO A Fundamental 1">4 ANO A Fundamental 1</option>
                <option value="4 ANO B Fundamental 1">4 ANO B Fundamental 1</option>
                <option value="4 ANO C Fundamental 1">4 ANO C Fundamental 1</option>
                <option value="4 ANO D Fundamental 1">4 ANO D Fundamental 1</option>
                <option value="5 ANO A Fundamental 1">5 ANO A Fundamental 1</option>
                <option value="5 ANO B Fundamental 1">5 ANO B Fundamental 1</option>
                <option value="5 ANO C Fundamental 1">5 ANO C Fundamental 1</option>
                <option value="5 ANO D Fundamental 1">5 ANO D Fundamental 1</option>
            </optgroup>
            <optgroup label="Fundamental 2">
                <option value="6 ANO A Fundamental 2">6 ANO A Fundamental 2</option>
                <option value="6 ANO B Fundamental 2">6 ANO B Fundamental 2</option>
                <option value="6 ANO C Fundamental 2">6 ANO C Fundamental 2</option>
                <option value="6 ANO D Fundamental 2">6 ANO D Fundamental 2</option>
                <option value="7 ANO A Fundamental 2">7 ANO A Fundamental 2</option>
                <option value="7 ANO B Fundamental 2">7 ANO B Fundamental 2</option>
                <option value="7 ANO C Fundamental 2">7 ANO C Fundamental 2</option>
                <option value="7 ANO D Fundamental 2">7 ANO D Fundamental 2</option>
                <option value="8 ANO A Fundamental 2">8 ANO A Fundamental 2</option>
                <option value="8 ANO B Fundamental 2">8 ANO B Fundamental 2</option>
                <option value="8 ANO C Fundamental 2">8 ANO C Fundamental 2</option>
                <option value="8 ANO D Fundamental 2">8 ANO D Fundamental 2</option>
                <option value="9 ANO A Fundamental 2">9 ANO A Fundamental 2</option>
                <option value="9 ANO B Fundamental 2">9 ANO B Fundamental 2</option>
                <option value="9 ANO C Fundamental 2">9 ANO C Fundamental 2</option>
                <option value="9 ANO D Fundamental 2">9 ANO D Fundamental 2</option>
            </optgroup>
            <optgroup label="Ensino Médio">
                <option value="1 ANO A Ensino Médio">1 ANO A Ensino Médio</option>
                <option value="1 ANO B Ensino Médio">1 ANO B Ensino Médio</option>
                <option value="1 ANO C Ensino Médio">1 ANO C Ensino Médio</option>
                <option value="1 ANO D Ensino Médio">1 ANO D Ensino Médio</option>
                <option value="2 ANO A Ensino Médio">2 ANO A Ensino Médio</option>
                <option value="2 ANO B Ensino Médio">2 ANO B Ensino Médio</option>
                <option value="2 ANO C Ensino Médio">2 ANO C Ensino Médio</option>
                <option value="2 ANO D Ensino Médio">2 ANO D Ensino Médio</option>
                <option value="3 ANO A Ensino Médio">3 ANO A Ensino Médio</option>
                <option value="3 ANO B Ensino Médio">3 ANO B Ensino Médio</option>
                <option value="3 ANO C Ensino Médio">3 ANO C Ensino Médio</option>
                <option value="3 ANO D Ensino Médio">3 ANO D Ensino Médio</option>
            </optgroup>
        </select>
    </div>
    <div>
        <label for="studentShift">Turno:</label>
        <select id="studentShift">
            <option value="">Selecione o Turno</option>
            <option value="Manhã">Manhã</option>
            <option value="Tarde">Tarde</option>
        </select>
    </div>
    <button class="button" onclick="addStudent()" type="button">Adicionar Aluno</button>
</div>
<div class="hidden" id="addDisciplineSection"> <h3>Adicionar Disciplina ao Aluno</h3>
<div>
<label for="disciplineClassSelect">Selecione a Turma:</label>
<select id="disciplineClassSelect">
<option value="">Selecione a Turma</option>
</select>
</div>
<div style="margin-top: 10px;">
<label for="studentSelect">Selecione o Aluno:</label>
<select disabled="" id="studentSelect"> <option value="">Selecione a Turma Primeiro</option>
</select>
</div>
<div style="margin-top: 10px;">
<label for="disciplineSelect">Selecione a Disciplina:</label>
<select id="disciplineSelect">
<option value="">Selecione a Disciplina</option>
</select>
</div>
<div style="margin-top: 10px;">
<label for="unitSelect">Selecione a Unidade:</label>
<select id="unitSelect">
<option value="">Selecione a Unidade</option>
<option value="1">1° Unidade</option>
<option value="2">2° Unidade</option>
<option value="3">3° Unidade</option>
<option value="4">4° Unidade</option>
</select>
</div>
<div style="margin-top: 10px;">
<label for="test1">Teste 1 (0-10):</label>
<select id="test1">
    <option value="">Nota Teste 1</option>
</select>
</div>
<div style="margin-top: 10px;">
<label for="test2">Teste 2 (0-10):</label>
<select id="test2">
    <option value="">Nota Teste 2</option>
</select>
</div>
<div style="margin-top: 10px;">
<label for="evaluation1">Avaliação (0-10):</label>
<select id="evaluation1">
    <option value="">Nota Avaliação</option>
</select>
</div>
<div style="margin-top: 10px;">
    <label>Média:</label>
    <span id="mediaDisplay">-</span>
</div>
<div style="margin-top: 10px;">
<label for="finalGrade">Menção Final:</label>
<select id="finalGrade">
<option value="">Menção Final</option>
<option value="Aprovado">Aprovado</option>
<option value="Recuperacao">Recuperação</option>
<option value="Reprovado">Reprovado</option>
</select>
</div>
<div style="margin-top: 10px;">
<label for="observationInput">Observações (Opcional):</label>
<input id="observationInput" placeholder="Observações (Opcional)" type="text"/>
</div>
<button class="button" onclick="addDiscipline()" style="margin-top: 15px;" type="button">Adicionar Disciplina</button>
</div>
<h2>Consultar Alunos</h2>
<input id="searchName" placeholder="Pesquisar Aluno" type="text"/>
<button class="button" onclick="searchStudent()" type="button">Pesquisar</button>
<h3>Imprimir Boletim</h3>
<div id="printControls">
<div>
<label for="printClassSelect" class="admin-print-label">Selecione a Turma:</label>
<select id="printClassSelect">
<option value="">Selecione a Turma</option>
</select>
</div>
<div style="margin-top: 10px;">
<label for="studentSelectPrint" class="admin-print-label">Selecione o Aluno (Opcional para impressão da turma):</label>
<select disabled="" id="studentSelectPrint"> <option value="">Selecione a Turma Primeiro</option>
</select>
</div>
<div style="margin-top: 10px;">
<label class="admin-print-label">Selecione as Unidades:</label>
<div>
<label><input class="unitCheckbox" type="checkbox" value="1" checked/> Unidade 1</label>
<label><input class="unitCheckbox" type="checkbox" value="2" checked/> Unidade 2</label>
<label><input class="unitCheckbox" type="checkbox" value="3" checked/> Unidade 3</label>
<label><input class="unitCheckbox" type="checkbox" value="4" checked/> Unidade 4</label>
</div>
</div>
<div style="margin-top: 10px;">
<label class="admin-print-label"><input name="reportType" type="radio" value="full" checked/> Incluir Avaliações</label>
<label class="admin-print-label"><input name="reportType" type="radio" value="summary"/> Somente Menção e Situação</label>
</div>
<button class="button" onclick="printStudentReport()" type="button">Imprimir Boletim do Aluno</button>
<button class="button" onclick="printClassReports()" type="button">Imprimir Boletins da Turma</button>
<button class="button" onclick="printAllReports()" type="button">Imprimir Todos os Boletins (Todos Alunos)</button>
</div>
<h3>Backup/Restaurar Dados (Manual)</h3>
<button class="button" onclick="exportData()" type="button">Exportar Dados (Backup)</button>
<div style="margin-top: 10px; border: 1px solid yellow; padding: 10px; border-radius: 5px;">
<p style="margin-top: 0; font-weight: bold;">Importar Dados:</p>
<input accept=".json" id="importFile" style="display:none;" type="file"/>
<button class="button" onclick="document.getElementById('importFile').click()" style="width: auto; display: inline-block; margin: 5px 0;" type="button">Selecionar Arquivo</button>
<span id="importFileName" style="margin-left: 10px; font-style: italic;">Nenhum arquivo selecionado.</span>
<button class="button delete-button" disabled="" id="performImportButton" onclick="importData()" style="width: auto; display: inline-block; margin: 5px;" type="button">Confirmar Importação (Irá substituir dados atuais!)</button>
<p class="error" id="importStatus" style="margin-top: 5px;"></p>
</div>
<table id="studentTable">
<thead>
<tr>
<th>Matrícula</th>
<th>Nome</th>
<th>Curso</th>
<th>Turma</th>
<th>Disciplina</th>
<th>Unidade</th>
<th>Teste 1</th>
<th>Teste 2</th>
<th>Avaliação</th>
<th>Média</th>
<th>Menção Final</th>
<th>Situação</th>
<th>Observações</th>
<th>Ações</th>
</tr>
</thead>
<tbody>
</tbody>
</table>
</div>
<div class="hidden" id="manageUsersSection">
<h1>Gerenciar Professores e Coordenadores</h1>
<button class="button" onclick="showStudentManagementSection()" style="width:auto; margin-bottom: 20px;" type="button">Voltar para Gerenciar Alunos</button>
<p class="security-warning">AVISO DE SEGURANÇA: As senhas estão visíveis nesta tela apenas para demonstração. Em um sistema real, senhas nunca devem ser exibidas ou armazenadas em texto plano.</p>
<p id="noUsersMessage">Nenhum usuário (Professor ou Coordenador) cadastrado além do administrador principal.</p>
<table id="usersTable">
<thead>
<tr>
<th>Nome</th>
<th>Usuário</th>
<th>Papel</th>
<th>Disciplinas Atribuídas</th>
<th>Turmas Atribuídas</th>
<th>Senha</th>
<th>Ações</th>
</tr>
</thead>
<tbody>
</tbody>
</table>
</div>
<div class="hidden" id="professorSection">
<h1 id="professorWelcome">Olá, Professor(a)!</h1>
<p>Selecione a disciplina, turma e unidade para lançar ou editar as notas dos alunos.</p>
<div>
<label for="professorDisciplineSelect">Disciplina:</label>
<select id="professorDisciplineSelect">
<option value="">Selecione a Disciplina</option>
</select>
<label for="professorClassSelect" style="margin-left: 20px;">Turma:</label>
<select id="professorClassSelect">
<option value="">Selecione a Turma</option>
</select>
<label for="professorUnitSelect" style="margin-left: 20px;">Unidade:</label>
<select id="professorUnitSelect">
<option value="">Selecione a Unidade</option>
<option value="1">1° Unidade</option>
<option value="2">2° Unidade</option>
<option value="3">3° Unidade</option>
<option value="4">4° Unidade</option>
</select>
</div>
<table class="professor-table" id="professorStudentTable" style="margin-top: 20px;">
<thead>
<tr>
<th>Matrícula</th>
<th>Nome do Aluno</th>
<th>Curso</th>
<th>Turno</th>
<th>Teste 1</th>
<th>Teste 2</th>
<th>Avaliação</th>
<th>Média</th>
<th>Menção Final</th>
<th>Situação</th>
<th>Observações</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<p id="professorNoStudentsMessage" style="text-align: center; font-style: italic; margin-top: 20px;">Selecione a disciplina, turma e unidade acima para ver os alunos.</p>
</div>

<div class="hidden" id="professorNotesSection">
    <h1>Agenda de Anotações do Professor</h1>
    <p>Adicione anotações para os alunos por disciplina e unidade. Estas anotações ficarão visíveis no boletim do aluno.</p>

    <div class="note-controls" style="margin-bottom: 20px;">
        <label for="notesDisciplineSelect">Disciplina:</label>
        <select id="notesDisciplineSelect">
            <option value="">Selecione a Disciplina</option>
            </select>

        <label for="notesClassSelect">Turma:</label>
        <select id="notesClassSelect">
            <option value="">Selecione a Turma</option>
            </select>

        <label for="notesStudentSelect">Aluno:</label>
        <select id="notesStudentSelect">
            <option value="">Selecione o Aluno</option>
            </select>

        <label for="notesUnitSelect">Unidade:</label>
        <select id="notesUnitSelect">
            <option value="">Selecione a Unidade</option>
            <option value="1">1° Unidade</option>
            <option value="2">2° Unidade</option>
            <option value="3">3° Unidade</option>
            <option value="4">4° Unidade</option>
        </select>
    </div>

    <h3>Nova Anotação</h3>
    <textarea id="professorNoteContent" placeholder="Escreva sua anotação aqui..."></textarea>
    <button class="button" onclick="saveProfessorNote()" style="width: auto; margin-top: 10px;" type="button">Salvar Anotação</button>

    <div class="note-display">
        <h3>Anotações Existentes</h3>
        <div id="existingProfessorNotes">
            <p class="no-notes" style="text-align: center; font-style: italic;">Nenhuma anotação encontrada para esta seleção.</p>
        </div>
    </div>
</div>

</div>
<footer id="appFooter">Escola Academia Primeiros Passos</footer>
</div>
<div class="modal hidden" id="addProfessorModal">
<div class="modal-content">
<span class="close-button" onclick="closeAddProfessorModal()">×</span>
<h2>Adicionar Novo Professor</h2>
<div>
<label for="newProfessorNameInput">Nome Completo:</label>
<input id="newProfessorNameInput" placeholder="Nome completo do professor" type="text"/>
</div>
<div>
<label for="newProfessorUsernameInput">Usuário (Login):</label>
<input id="newProfessorUsernameInput" placeholder="Nome de usuário para login" type="text"/>
</div>
<div>
<label for="newProfessorPasswordInput">Senha:</label>
<input id="newProfessorPasswordInput" placeholder="Senha para login" type="password"/>
</div>
<h3>Atribuições por Disciplina e Turma:</h3>
<div id="newProfessorAssignments">
    </div>
<button class="button" onclick="saveProfessor()" style="width: auto; display: inline-block; margin-top:20px;" type="button">Salvar Professor</button>
</div>
</div>
<div class="modal hidden" id="addCoordinatorModal">
<div class="modal-content">
<span class="close-button" onclick="closeAddCoordenadorModal()">×</span>
<h2>Adicionar Novo Coordenador</h2>
<div>
<label for="newCoordinatorNameInput">Nome Completo:</label>
<input id="newCoordinatorNameInput" placeholder="Nome completo do coordenador" type="text"/>
</div>
<div>
<label for="newCoordinatorUsernameInput">Usuário (Login):</label>
<input id="newCoordinatorUsernameInput" placeholder="Nome de usuário para login" type="text"/>
</div>
<div>
<label for="newCoordinatorPasswordInput">Senha:</label>
<input id="newCoordinatorPasswordInput" placeholder="Senha para login" type="password"/>
</div>
<p style="margin-top: 15px; color: #A52A2A;">Coordenadores têm acesso total ao sistema, exceto a criação/edição de usuários.</p>
<button class="button" onclick="saveCoordinator()" style="width: auto; display: inline-block; margin-top:20px;" type="button">Salvar Coordenador</button>
</div>
</div>
<div class="modal hidden" id="editUserModal">
<div class="modal-content">
<span class="close-button" onclick="closeEditUserModal()">×</span>
<h2 id="editUserModalTitle">Editar Usuário</h2>
<input id="editUserOriginalUsername" type="hidden"/>
<input id="editUserRole" type="hidden"/>
<div>
<label for="editUserNameInput">Nome Completo:</label>
<input id="editUserNameInput" placeholder="Nome completo" type="text"/>
</div>
<div>
<label for="editUserUsernameInput">Usuário (Login):</label>
<input id="editUserUsernameInput" placeholder="Nome de usuário para login" type="text"/>
<small style="display: block; margin-top: 5px; color: #A52A2A;">Alterar o usuário pode exigir um novo login.</small>
</div>
<div>
<label for="editUserPasswordInput">Senha:</label>
<input id="editUserPasswordInput" placeholder="Deixe em branco para manter a senha atual" type="password"/>
<small style="display: block; margin-top: 5px; color: #A52A2A;">Deixe este campo em branco para não alterar a senha.</small>
</div>
<div id="editProfessorAssignments">
<h3>Atribuições por Disciplina e Turma:</h3>
    </div>
<button class="button" onclick="updateUser()" style="width: auto; display: inline-block; margin-top:20px;" type="button">Atualizar Usuário</button>
</div>
</div>
<script>
    // Generate an array of numbers from 0 to 10 with increments of 0.25
    const gradeOptions = [];
    for (let i = 0; i <= 10; i += 0.25) {
        gradeOptions.push(i.toFixed(2)); // Ensure two decimal places, e.g., "1.00", "1.25"
    }

    // Function to populate a grade select element
    function populateGradeSelect(selectId) {
        const selectElement = document.getElementById(selectId);
        if (!selectElement) return;

        selectElement.innerHTML = '<option value="">Nota ' + selectId.replace('test', 'Teste ').replace('evaluation1', 'Avaliação') + '</option>';
        gradeOptions.forEach(grade => {
            const option = document.createElement('option');
            option.value = grade;
            option.textContent = grade.replace('.', ','); // Display with comma
            selectElement.appendChild(option);
        });
    }

    // --- DATA SIMULATION IN MEMORY (Replace with Local Storage or Backend) ---
    // Initial data (will be replaced by localStorage if data exists)
     let students = [];
     let users = [{ username: 'administrador', password: 'admsenac2024', role: 'admin', name: 'Administrador', assignments: [] }]; // Default admin user

    const classInfoMap = {
        // Educação Infantil
        'ED. Infantil 1 Turma A': { unit: 'Manhã', course: 'Educação Infantil' },
        'ED. Infantil 1 Turma B': { unit: 'Manhã', course: 'Educação Infantil' },
        'ED. Infantil 1 Turma C': { unit: 'Manhã', course: 'Educação Infantil' },
        'ED. Infantil 1 Turma D': { unit: 'Manhã', course: 'Educação Infantil' },
        'ED. Infantil 2 Turma A': { unit: 'Manhã', course: 'Educação Infantil' },
        'ED. Infantil 2 Turma B': { unit: 'Manhã', course: 'Educação Infantil' },
        'ED. Infantil 2 Turma C': { unit: 'Manhã', course: 'Educação Infantil' },
        'ED. Infantil 2 Turma D': { unit: 'Manhã', course: 'Educação Infantil' },
        'ED. Infantil 3 Turma A': { unit: 'Manhã', course: 'Educação Infantil' },
        'ED. Infantil 3 Turma B': { unit: 'Manhã', course: 'Educação Infantil' },
        'ED. Infantil 3 Turma C': { unit: 'Manhã', course: 'Educação Infantil' },
        'ED. Infantil 3 Turma D': { unit: 'Manhã', course: 'Educação Infantil' },

        // Fundamental 1
        '1 ANO A Fundamental 1': { unit: 'Manhã', course: 'Fundamental 1' },
        '1 ANO B Fundamental 1': { unit: 'Manhã', course: 'Fundamental 1' },
        '1 ANO C Fundamental 1': { unit: 'Manhã', course: 'Fundamental 1' },
        '1 ANO D Fundamental 1': { unit: 'Manhã', course: 'Fundamental 1' },
        '2 ANO A Fundamental 1': { unit: 'Manhã', course: 'Fundamental 1' },
        '2 ANO B Fundamental 1': { unit: 'Manhã', course: 'Fundamental 1' },
        '2 ANO C Fundamental 1': { unit: 'Manhã', course: 'Fundamental 1' },
        '2 ANO D Fundamental 1': { unit: 'Manhã', course: 'Fundamental 1' },
        '3 ANO A Fundamental 1': { unit: 'Manhã', course: 'Fundamental 1' },
        '3 ANO B Fundamental 1': { unit: 'Manhã', course: 'Fundamental 1' },
        '3 ANO C Fundamental 1': { unit: 'Manhã', course: 'Fundamental 1' },
        '3 ANO D Fundamental 1': { unit: 'Manhã', course: 'Fundamental 1' },
        '4 ANO A Fundamental 1': { unit: 'Manhã', course: 'Fundamental 1' },
        '4 ANO B Fundamental 1': { unit: 'Manhã', course: 'Fundamental 1' },
        '4 ANO C Fundamental 1': { unit: 'Manhã', course: 'Fundamental 1' },
        '4 ANO D Fundamental 1': { unit: 'Manhã', course: 'Fundamental 1' },
        '5 ANO A Fundamental 1': { unit: 'Manhã', course: 'Fundamental 1' },
        '5 ANO B Fundamental 1': { unit: 'Manhã', course: 'Fundamental 1' },
        '5 ANO C Fundamental 1': { unit: 'Manhã', course: 'Fundamental 1' },
        '5 ANO D Fundamental 1': { unit: 'Manhã', course: 'Fundamental 1' },

        // Fundamental 2
        '6 ANO A Fundamental 2': { unit: 'Manhã', course: 'Fundamental 2' },
        '6 ANO B Fundamental 2': { unit: 'Manhã', course: 'Fundamental 2' },
        '6 ANO C Fundamental 2': { unit: 'Manhã', course: 'Fundamental 2' },
        '6 ANO D Fundamental 2': { unit: 'Manhã', course: 'Fundamental 2' },
        '7 ANO A Fundamental 2': { unit: 'Manhã', course: 'Fundamental 2' },
        '7 ANO B Fundamental 2': { unit: 'Manhã', course: 'Fundamental 2' },
        '7 ANO C Fundamental 2': { unit: 'Manhã', course: 'Fundamental 2' },
        '7 ANO D Fundamental 2': { unit: 'Manhã', course: 'Fundamental 2' },
        '8 ANO A Fundamental 2': { unit: 'Manhã', course: 'Fundamental 2' },
        '8 ANO B Fundamental 2': { unit: 'Manhã', course: 'Fundamental 2' },
        '8 ANO C Fundamental 2': { unit: 'Manhã', course: 'Fundamental 2' },
        '8 ANO D Fundamental 2': { unit: 'Manhã', course: 'Fundamental 2' },
        '9 ANO A Fundamental 2': { unit: 'Manhã', course: 'Fundamental 2' },
        '9 ANO B Fundamental 2': { unit: 'Manhã', course: 'Fundamental 2' },
        '9 ANO C Fundamental 2': { unit: 'Manhã', course: 'Fundamental 2' },
        '9 ANO D Fundamental 2': { unit: 'Manhã', course: 'Fundamental 2' },

        // Ensino Médio
        '1 ANO A Ensino Médio': { unit: 'Manhã', course: 'Ensino Médio' },
        '1 ANO B Ensino Médio': { unit: 'Manhã', course: 'Ensino Médio' },
        '1 ANO C Ensino Médio': { unit: 'Manhã', course: 'Ensino Médio' },
        '1 ANO D Ensino Médio': { unit: 'Manhã', course: 'Ensino Médio' },
        '2 ANO A Ensino Médio': { unit: 'Manhã', course: 'Ensino Médio' },
        '2 ANO B Ensino Médio': { unit: 'Manhã', course: 'Ensino Médio' },
        '2 ANO C Ensino Médio': { unit: 'Manhã', course: 'Ensino Médio' },
        '2 ANO D Ensino Médio': { unit: 'Manhã', course: 'Ensino Médio' },
        '3 ANO A Ensino Médio': { unit: 'Manhã', course: 'Ensino Médio' },
        '3 ANO B Ensino Médio': { unit: 'Manhã', course: 'Ensino Médio' },
        '3 ANO C Ensino Médio': { unit: 'Manhã', course: 'Ensino Médio' },
        '3 ANO D Ensino Médio': { unit: 'Manhã', course: 'Ensino Médio' },
    };

    function getClassInfo(className) { return classInfoMap[className] || { unit: 'Desconhecido', course: 'Desconhecido' }; }

    // --- Local Storage Functions ---
    function saveData() {
        try {
            localStorage.setItem('students', JSON.stringify(students));
            localStorage.setItem('users', JSON.stringify(users));
             // console.log('Data saved to localStorage');
        } catch (e) {
            console.error('Error saving data to localStorage:', e);
            alert('Não foi possível salvar os dados no navegador. Por favor, verifique se o armazenamento local está ativado.');
        }
    }

    function loadData() {
        try {
            const savedStudents = localStorage.getItem('students');
            const savedUsers = localStorage.getItem('users');
            if (savedStudents) {
                students = JSON.parse(savedStudents);
                // Ensure students have a unique ID if they don't already (for backward compatibility)
                if (students.length > 0) {
                     students = students.map((s, index) => {
                         if (!s.id) s.id = 's' + (index + 1);
                         if (!s.professorNotes) s.professorNotes = []; // NEW: Ensure professorNotes array exists
                         // NEW: Ensure existing students have 'matricula' for backward compatibility
                         if (!s.matricula) s.matricula = ''; // Default to empty string
                         return s;
                     });
                }
                 // console.log('Students data loaded from localStorage');
            } else {
                 // Populate with initial student data if no data in localStorage
                 populateInitialStudents();
                 // console.log('No student data found in localStorage, using initial data.');
            }

            if (savedUsers) {
                users = JSON.parse(savedUsers);
                 // Ensure the default admin user exists if loading from a state where it might be missing
                 if (!users.find(user => user.username === 'administrador')) {
                     users.unshift({ username: 'administrador', password: 'admsenac2024', role: 'admin', name: 'Administrador', assignments: [] });
                 }
                 // NEW: Ensure all users have an assignments array if missing
                 users = users.map(user => {
                     if (!Array.isArray(user.assignments)) user.assignments = [];
                     return user;
                 });
                 // console.log('Users data loaded from localStorage');
            } else {
                 // Add initial professor and coordinator data if no user data in localStorage
                 users = [{ username: 'administrador', password: 'admsenac2024', role: 'admin', name: 'Administrador', assignments: [] }];
                 users.push({ username: 'profmath', password: 'passprof', role: 'professor', name: 'Prof. Matemática', assignments: [{ discipline: 'Matemática', classes: ['1 ANO A Fundamental 1', '1 ANO B Fundamental 1', '1 ANO C Fundamental 1', '2 ANO A Fundamental 1', '2 ANO B Fundamental 1', '3 ANO A Fundamental 1'] }, { discipline: 'Física', classes: ['2 ANO A Fundamental 1', '2 ANO B Fundamental 1'] }] });
                 users.push({ username: 'coord', password: 'passcoord', role: 'coordenador', name: 'Coordenador Geral', assignments: [] });
                  // console.log('No user data found in localStorage, using initial data.');
            }
        } catch (e) {
            console.error('Error loading data from localStorage:', e);
            alert('Não foi possível carregar os dados do navegador. Os dados iniciais serão usados.');
             // Fallback to initial data if loading fails
            students = [];
            users = [{ username: 'administrador', password: 'admsenac2024', role: 'admin', name: 'Administrador', assignments: [] }];
             populateInitialStudents();
             users.push({ username: 'profmath', password: 'passprof', role: 'professor', name: 'Prof. Matemática', assignments: [{ discipline: 'Matemática', classes: ['1 ANO A Fundamental 1', '1 ANO B Fundamental 1', '1 ANO C Fundamental 1', '2 ANO A Fundamental 1', '2 ANO B Fundamental 1', '3 ANO A Fundamental 1'] }, { discipline: 'Física', classes: ['2 ANO A Fundamental 1', '2 ANO B Fundamental 1'] }] });
             users.push({ username: 'coord', password: 'passcoord', role: 'coordenador', name: 'Coordenador Geral', assignments: [] });
        }
    }

     // Helper to populate initial student data (only used if no data in localStorage)
     function populateInitialStudents() {
        students = []; // Clear existing students if any
         // Example of populating initial students if needed, based on the new class structure.
         // For now, leaving it empty as previous students were specific to 'Médio Técnico'.
         // If you want to pre-populate with students from new classes, you can add similar logic here.
     }


    let currentUser = null;
    const loginContainer = document.getElementById('loginContainer');
    const appContainer = document.getElementById('appContainer');
    const studentManagementSection = document.getElementById('studentManagementSection');
    const manageUsersSection = document.getElementById('manageUsersSection');
    const professorSection = document.getElementById('professorSection');
    const professorNotesSection = document.getElementById('professorNotesSection'); // NEW
    const userManagementSection = document.getElementById('userManagementSection');
    const sidebarHr = document.getElementById('sidebarHr');
    const professorWelcome = document.getElementById('professorWelcome');
    const studentBulletinSection = document.getElementById('studentBulletinSection');
    const studentPrintOptions = document.getElementById('studentPrintOptions'); // Container for student's print options
    const professorAgendaButton = document.getElementById('professorAgendaButton'); // NEW


    function showSection(sectionToShow) {
        studentManagementSection.classList.add('hidden');
        manageUsersSection.classList.add('hidden');
        professorSection.classList.add('hidden');
        studentBulletinSection.classList.add('hidden');
        professorNotesSection.classList.add('hidden'); // NEW
        sectionToShow.classList.remove('hidden');
    }

    function showStudentManagementSection() {
        showSection(studentManagementSection);
        renderStudentTable(students);
        populateClassSelect(document.getElementById('printClassSelect'));
        populateStudentPrintSelect();
        if (currentUser && (currentUser.role === 'admin' || currentUser.role === 'coordenador')) {
            document.getElementById('addStudentSection').classList.remove('hidden');
            document.getElementById('addDisciplineSection').classList.remove('hidden');
            populateClassSelect(document.getElementById('disciplineClassSelect'));
            populateStudentSelectForDiscipline();
            populateDisciplineSelect(document.getElementById('disciplineSelect')); // Populate discipline select
            populateGradeSelect('test1'); // Populate grade selects
            populateGradeSelect('test2');
            populateGradeSelect('evaluation1');
            professorAgendaButton.classList.add('hidden'); // NEW: Hide agenda button for admin/coordinator
        } else {
            document.getElementById('addStudentSection').classList.add('hidden');
            document.getElementById('addDisciplineSection').classList.add('hidden');
        }
    }

    function showManageUsersSection() {
        showSection(manageUsersSection);
        renderUsersTable(users);
        professorAgendaButton.classList.add('hidden'); // NEW
    }

    function showProfessorSection(user) {
        showSection(professorSection);
        professorWelcome.textContent = 'Olá, ' + user.name + '!';
        populateProfessorSelects(user);
        document.querySelector('#professorStudentTable tbody').innerHTML = '';
        document.getElementById('professorNoStudentsMessage').classList.remove('hidden');
         document.querySelector('#professorStudentTable thead').classList.add('hidden'); // Hide table header initially
        professorAgendaButton.classList.remove('hidden'); // NEW: Show agenda button for professor
    }

    // NEW: Function to show Professor Notes Section
    function showProfessorNotesSection() {
        showSection(professorNotesSection);
        professorAgendaButton.classList.remove('hidden'); // Keep agenda button visible
        populateProfessorNotesControls();
        document.getElementById('professorNoteContent').value = ''; // Clear textarea
        document.getElementById('existingProfessorNotes').innerHTML = '<p class="no-notes" style="text-align: center; font-style: italic;">Selecione aluno, disciplina e unidade para ver ou adicionar anotações.</p>'; // Clear existing notes
    }


    function showStudentBulletin() {
        showSection(studentBulletinSection);
        if (currentUser && currentUser.role === 'aluno') {
            const student = students.find(s => s.id === currentUser.studentId);
            const bulletinContentDiv = document.getElementById('studentBulletinContent');
            if (student) {
                // Load all units by default for initial display
                const allUnits = [...new Set(student.disciplines.map(d => d.unit))].sort((a, b) => a - b);
                const bulletinHTML = generateBulletinHTML(student, allUnits, 'full'); // Display full, all units
                bulletinContentDiv.innerHTML = bulletinHTML;

                // Make print options visible
                if(studentPrintOptions) studentPrintOptions.classList.remove('hidden');
                // Check all unit checkboxes by default for the student
                document.querySelectorAll('.studentUnitCheckboxPrint').forEach(cb => cb.checked = true);
                // Set default report type for student
                const studentReportTypeFull = document.querySelector('input[name="studentReportType"][value="full"]');
                if(studentReportTypeFull) studentReportTypeFull.checked = true;

                displayStudentNotes(student); // NEW: Display professor notes for the student

            } else {
                bulletinContentDiv.innerHTML = '<p style="text-align: center; font-style: italic;">Não foi possível encontrar seus dados de boletim.</p>';
                if(studentPrintOptions) studentPrintOptions.classList.add('hidden');
                document.getElementById('studentNotesContent').innerHTML = '<p class="no-notes">Nenhuma anotação disponível.</p>'; // NEW: Clear student notes
            }
        } else {
            bulletinContentDiv.innerHTML = '<p style="text-align: center; font-style: italic;">Você precisa estar logado como aluno para ver seu boletim.</p>';
             if(studentPrintOptions) studentPrintOptions.classList.add('hidden');
             document.getElementById('studentNotesContent').innerHTML = '<p class="no-notes">Nenhuma anotação disponível.</p>'; // NEW: Clear student notes
        }
        userManagementSection.classList.add('hidden');
        sidebarHr.classList.add('hidden');
        professorAgendaButton.classList.add('hidden'); // NEW
    }


    function goHome() {
        if (currentUser) {
            if (currentUser.role === 'admin' || currentUser.role === 'coordenador') {
                showStudentManagementSection();
                userManagementSection.classList.remove('hidden');
                sidebarHr.classList.remove('hidden');
                professorAgendaButton.classList.add('hidden'); // NEW
            } else if (currentUser.role === 'professor') {
                showProfessorSection(currentUser);
                userManagementSection.classList.add('hidden');
                sidebarHr.classList.add('hidden');
                professorAgendaButton.classList.remove('hidden'); // NEW
            } else if (currentUser.role === 'aluno') {
                showStudentBulletin();
                userManagementSection.classList.add('hidden');
                sidebarHr.classList.add('hidden');
                professorAgendaButton.classList.add('hidden'); // NEW
            }
        } else {
            logout();
        }
    }


    function logout() {
        currentUser = null;
        localStorage.removeItem('currentUser');
        appContainer.classList.add('hidden');
        loginContainer.classList.remove('hidden');
        document.getElementById('username').value = '';
        document.getElementById('password').value = '';
        document.getElementById('loginError').textContent = '';
        userManagementSection.classList.add('hidden');
        sidebarHr.classList.add('hidden');
        professorAgendaButton.classList.add('hidden'); // NEW
        document.querySelector('#studentTable tbody').innerHTML = '';
        document.querySelector('#usersTable tbody').innerHTML = '';
        document.querySelector('#professorStudentTable tbody').innerHTML = '';
        document.getElementById('addStudentSection').classList.add('hidden');
        document.getElementById('addDisciplineSection').classList.add('hidden');
        document.getElementById('studentBulletinContent').innerHTML = '<p style="text-align: center; font-style: italic;">Carregando boletim...</p>';
        if(studentPrintOptions) studentPrintOptions.classList.add('hidden'); // Hide student print options on logout
        document.getElementById('studentNotesContent').innerHTML = '<p class="no-notes">Nenhuma anotação disponível.</p>'; // NEW: Clear student notes
    }

    document.getElementById('loginButton').addEventListener('click', function() {
        const usernameInput = document.getElementById('username');
        const passwordInput = document.getElementById('password');
        const loginError = document.getElementById('loginError');
        const username = usernameInput.value;
        const password = passwordInput.value;
        loginError.textContent = '';
        let foundUser = users.find(user => user.username === username && user.password === password);
        if (foundUser) {
            currentUser = foundUser;
            // Only store non-sensitive data in localStorage for currentUser state
            localStorage.setItem('currentUser', JSON.stringify({ username: foundUser.username, role: foundUser.role }));
            loginContainer.classList.add('hidden');
            appContainer.classList.remove('hidden');
            if (currentUser.role === 'admin' || currentUser.role === 'coordenador') {
                showStudentManagementSection();
                userManagementSection.classList.remove('hidden');
                sidebarHr.classList.remove('hidden');
                professorAgendaButton.classList.add('hidden'); // NEW
            } else if (currentUser.role === 'professor') {
                showProfessorSection(currentUser);
                userManagementSection.classList.add('hidden');
                sidebarHr.classList.add('hidden');
                professorAgendaButton.classList.remove('hidden'); // NEW
            } else if (currentUser.role === 'aluno') {
                 // Find the corresponding student data
                const student = students.find(s => s.id === currentUser.studentId || (s.matricula && s.matricula.trim().toLowerCase() === currentUser.username.trim().toLowerCase())); // Link by studentId first, then matricula/username
                if (student) {
                    currentUser.studentId = student.id; // Link student user to student data
                }
                showStudentBulletin();
                userManagementSection.classList.add('hidden');
                sidebarHr.classList.add('hidden');
                professorAgendaButton.classList.add('hidden'); // NEW
            }
        }
        else {
            loginError.textContent = 'Usuário ou senha inválidos.';
        }
    });

    window.addEventListener('load', function() {
        loadData(); // Load data first
        // No longer need to call updateStudentShiftDisplay on load if it's a direct input
        // updateStudentShiftDisplay();

        const savedUser = JSON.parse(localStorage.getItem('currentUser'));
        if (savedUser) {
            // Find the full user object from the loaded users data
            currentUser = users.find(user => user.username === savedUser.username && user.role === savedUser.role);
             if (currentUser && currentUser.role === 'aluno') {
                const student = students.find(s => s.id === currentUser.studentId || (s.matricula && s.matricula.trim().toLowerCase() === currentUser.username.trim().toLowerCase())); // Link by studentId first, then matricula/username
                 if (student) {
                    currentUser.studentId = student.id; // Link student user to student data
                 } else {
                     console.error('Aluno data not found for logged in user:', currentUser.name);
                     // Optionally log out the user if student data is essential
                     logout();
                     return; // Stop further execution if student data is missing for an aluno user
                 }
            }
            if (currentUser) {
                appContainer.classList.remove('hidden');
                loginContainer.classList.add('hidden');
                if (currentUser.role === 'admin' || currentUser.role === 'coordenador') {
                    showStudentManagementSection();
                    userManagementSection.classList.remove('hidden');
                    sidebarHr.classList.remove('hidden');
                    professorAgendaButton.classList.add('hidden'); // NEW
                } else if (currentUser.role === 'professor') {
                    showProfessorSection(currentUser);
                    userManagementSection.classList.add('hidden');
                    sidebarHr.classList.add('hidden');
                    professorAgendaButton.classList.remove('hidden'); // NEW
                } else if (currentUser.role === 'aluno') {
                    showStudentBulletin();
                    userManagementSection.classList.add('hidden');
                    sidebarHr.classList.add('hidden');
                    professorAgendaButton.classList.add('hidden'); // NEW
                }
            } else {
                logout(); // Logout if saved user data is invalid or not found in loaded users
            }
        } else {
            loginContainer.classList.remove('hidden');
            appContainer.classList.add('hidden');
        }
    });


    function renderStudentTable(studentsToRender) {
        const tableBody = document.querySelector('#studentTable tbody');
        tableBody.innerHTML = '';
        if (!studentsToRender || studentsToRender.length === 0) {
            const colspan = 14; // Updated for new columns: Matrícula + Média
            const row = tableBody.insertRow();
            const cell = row.insertCell();
            cell.colSpan = colspan;
            cell.textContent = "Nenhum aluno encontrado.";
            cell.style.textAlign = 'center';
            cell.style.fontStyle = 'italic';
            return;
        }
        studentsToRender.forEach(student => {
            const sortedDisciplines = student.disciplines.sort((a, b) => a.unit - b.unit);
            if (sortedDisciplines.length === 0) {
                const row = tableBody.insertRow();
                row.classList.add('student-group-header');
                row.insertCell().textContent = student.matricula || '-'; // Display matricula
                row.insertCell().textContent = student.name;
                row.insertCell().textContent = student.course;
                row.insertCell().textContent = student.class;
                const emptyCell = row.insertCell();
                emptyCell.colSpan = 9; // Matrícula, Name, Course, Class are 4. Total 14. 14-4=10. Ações is 1. so 14-5 = 9
                emptyCell.textContent = "Nenhuma disciplina adicionada.";
                emptyCell.style.textAlign = 'center';
                emptyCell.style.fontStyle = 'italic';
                row.insertCell().textContent = ''; // For actions cell
            } else {
                sortedDisciplines.forEach((discipline, index) => {
                    const row = tableBody.insertRow();
                    row.classList.add('discipline-row');
                    if (index === 0) {
                        const matriculaCell = row.insertCell(); matriculaCell.textContent = student.matricula || '-'; matriculaCell.rowSpan = sortedDisciplines.length; matriculaCell.classList.add('student-group-header'); matriculaCell.style.verticalAlign = 'top';
                        const nameCell = row.insertCell(); nameCell.textContent = student.name; nameCell.rowSpan = sortedDisciplines.length; nameCell.classList.add('student-group-header'); nameCell.style.verticalAlign = 'top';
                        const courseCell = row.insertCell(); courseCell.textContent = student.course; courseCell.rowSpan = sortedDisciplines.length; courseCell.classList.add('student-group-header'); courseCell.style.verticalAlign = 'top';
                        const classCell = row.insertCell(); classCell.textContent = student.class; classCell.rowSpan = sortedDisciplines.length; classCell.classList.add('student-group-header'); classCell.style.verticalAlign = 'top';
                    }
                    row.insertCell().textContent = discipline.discipline;
                    row.insertCell().textContent = discipline.unit;
                    ['test1', 'test2', 'eval1', 'media', 'finalGrade', 'situation', 'observation'].forEach(field => { // Added media
                        const cell = row.insertCell(); cell.classList.add('editable-cell');
                        cell.dataset.studentId = student.id; cell.dataset.disciplineName = discipline.discipline; cell.dataset.unitNumber = discipline.unit; cell.dataset.field = field;
                        if (field === 'observation') cell.dataset.type = 'text';
                        else if (field === 'finalGrade') {
                            cell.dataset.type = 'select';
                            cell.dataset.options = ',"Aprovado","Recuperacao","Reprovado"';
                        } else if (field === 'situation') {
                             cell.dataset.type = 'select';
                             cell.dataset.options = ',"Aprovado","Recuperado","Recuperado","Pendente"'; // Added Recuperado as option
                        } else if (field === 'media') { // Media field should be display-only
                            cell.classList.remove('editable-cell'); // Remove editable class for media
                            cell.dataset.type = 'text'; // But still treat as text for display
                        }
                         else { // test1, test2, eval1 are numerical select
                            cell.dataset.type = 'select';
                            cell.dataset.options = gradeOptions.join(','); // Use generated grade options
                        }
                        // Display value: if it's media, round to 2 decimal places. Otherwise, use existing logic.
                        let displayValue = discipline[field];
                        if (field === 'media' && displayValue !== undefined && displayValue !== null && displayValue !== '') {
                            displayValue = parseFloat(displayValue).toFixed(2).replace('.', ','); // Display with comma
                        } else if (['test1', 'test2', 'eval1'].includes(field) && displayValue !== undefined && displayValue !== null && displayValue !== '') {
                            displayValue = String(displayValue).replace('.', ','); // Display numerical grades with comma
                        }
                        else if (displayValue === undefined || displayValue === null || displayValue === '') {
                            displayValue = (field === 'observation' || field === 'finalGrade' || field === 'situation') ? '' : '-';
                        }
                        cell.innerHTML = `<span>${displayValue}</span>`;
                    });
                    const actionsCell = row.insertCell();
                    actionsCell.innerHTML = `<button type="button" class="button delete-button" data-student-id="${student.id}" data-discipline-name="${discipline.discipline}" data-unit-number="${discipline.unit}">Excluir</button>`;
                });
            }
        });
        attachEditableCellListeners('#studentTable');
        attachDeleteButtonListeners('#studentTable');
    }

     // Modified renderProfessorTable to use the new assignments structure
    function renderProfessorTable(studentsToRender, selectedDiscipline, selectedClass, selectedUnit) {
        const tableBody = document.querySelector('#professorStudentTable tbody');
        tableBody.innerHTML = '';
        const professorAssignments = currentUser.assignments || [];
        const assignedClassesForDiscipline = professorAssignments
            .filter(assignment => assignment.discipline === selectedDiscipline)
            .flatMap(assignment => assignment.classes);

        if (!studentsToRender || studentsToRender.length === 0 || !assignedClassesForDiscipline.includes(selectedClass)) {
             document.getElementById('professorNoStudentsMessage').classList.remove('hidden');
            document.querySelector('#professorStudentTable thead').classList.add('hidden'); // Hide header if no students
             return;
        } else {
             document.getElementById('professorNoStudentsMessage').classList.remove('hidden');
             document.querySelector('#professorStudentTable thead').classList.remove('hidden'); // Show header if students are rendered
        }

        studentsToRender.forEach(student => {
            const disciplineData = student.disciplines.find(d => d.discipline === selectedDiscipline && d.unit == selectedUnit); // Use == for unit comparison due to string/number mix
            const row = tableBody.insertRow();
            row.insertCell().textContent = student.matricula || '-'; // Display matricula
            row.insertCell().textContent = student.name;
            row.insertCell().textContent = student.course;
            row.insertCell().textContent = student.unit;
            ['test1', 'test2', 'eval1', 'media', 'finalGrade', 'situation', 'observation'].forEach(field => { // Added media
                const cell = row.insertCell(); cell.classList.add('editable-cell');
                cell.dataset.studentId = student.id; cell.dataset.disciplineName = selectedDiscipline; cell.dataset.unitNumber = selectedUnit; cell.dataset.field = field;
                if (field === 'observation') cell.dataset.type = 'text';
                else if (field === 'finalGrade') {
                    cell.dataset.type = 'select';
                    cell.dataset.options = ',"Aprovado","Recuperacao","Reprovado"';
                } else if (field === 'situation') {
                    cell.dataset.type = 'select';
                    cell.dataset.options = ',"Aprovado","Recuperado","Recuperado","Pendente"'; // Added Recuperado as option
                } else if (field === 'media') { // Media field should be display-only
                    cell.classList.remove('editable-cell'); // Remove editable class for media
                    cell.dataset.type = 'text'; // But still treat as text for display
                }
                else { // test1, test2, eval1 are numerical select
                    cell.dataset.type = 'select';
                    cell.dataset.options = gradeOptions.join(','); // Use generated grade options
                }
                 // Display value: if it's media, round to 2 decimal places. Otherwise, use existing logic.
                let displayValue = disciplineData ? disciplineData[field] : undefined;
                if (field === 'media' && displayValue !== undefined && displayValue !== null && displayValue !== '') {
                    displayValue = parseFloat(displayValue).toFixed(2).replace('.', ','); // Display with comma
                } else if (['test1', 'test2', 'eval1'].includes(field) && displayValue !== undefined && displayValue !== null && displayValue !== '') {
                    displayValue = String(displayValue).replace('.', ','); // Display numerical grades with comma
                }
                else if (displayValue === undefined || displayValue === null || displayValue === '') {
                    displayValue = (field === 'observation' || field === 'finalGrade' || field === 'situation') ? '' : '-';
                }
                cell.innerHTML = `<span>${displayValue}</span>`;
            });
        });
        attachEditableCellListeners('#professorStudentTable');
    }


    // Modified renderUsersTable to display new professor assignments structure
    function renderUsersTable(usersToRender) {
        const tableBody = document.querySelector('#usersTable tbody');
        tableBody.innerHTML = '';
        const noUsersMessage = document.getElementById('noUsersMessage');
        const displayUsers = usersToRender.filter(user => user.username !== 'administrador');
        if (!displayUsers || displayUsers.length === 0) {
            noUsersMessage.classList.remove('hidden');
            document.getElementById('usersTable').classList.add('hidden');
        } else {
            noUsersMessage.classList.add('hidden'); // Corrected logic: hide message if there are users
            document.getElementById('usersTable').classList.remove('hidden');
            displayUsers.forEach(user => {
                const row = tableBody.insertRow();
                row.insertCell().textContent = user.name;
                row.insertCell().textContent = user.username;
                row.insertCell().textContent = user.role.charAt(0).toUpperCase() + user.role.slice(1);

                // Display professor assignments based on the new structure
                if (user.role === 'professor' && user.assignments) {
                    const disciplinesText = user.assignments.map(assignment => assignment.discipline).join(', ');
                    // Concatenate discipline and classes for display in a more readable way
                    const classesText = user.assignments.map(assignment => `${assignment.discipline}: ${assignment.classes.join(', ')}`).join('; ');

                    row.insertCell().textContent = disciplinesText || '-';
                    row.insertCell().textContent = classesText || '-';
                } else {
                    row.insertCell().textContent = '-'; // No disciplines for non-professors
                    row.insertCell().textContent = '-'; // No classes for non-professors
                }

                row.insertCell().textContent = user.password; // Display password for demonstration (should be removed in real app)
                const actionsCell = row.insertCell();

                // Always show edit/delete buttons for professors and coordinators, and delete for students
                 if (user.role !== 'admin') { // Admin cannot be edited/deleted here
                    actionsCell.innerHTML = `<button type="button" class="button" onclick="editUser('${user.username}')">Editar</button> <button type="button" class="button delete-button" onclick="deleteUser('${user.username}')">Excluir</button>`;
                 } else {
                    actionsCell.textContent = '-';
                 }
                 // Note: Edit for 'aluno' is currently limited in the modal, but the button is shown.
            });
        }
    }

    function attachEditableCellListeners(tableSelector) {
        const table = document.querySelector(tableSelector);
        if (!table) return;
        table.querySelectorAll('.editable-cell').forEach(cell => {
            const newCell = cell.cloneNode(true);
            cell.parentNode.replaceChild(newCell, cell);
        });
        table.querySelectorAll('.editable-cell').forEach(cell => {
            cell.removeEventListener('click', activateEditableCell); // Prevent multiple listeners
            cell.addEventListener('click', activateEditableCell);
        });
    }

    function activateEditableCell(event) {
        const cell = event.target.closest('.editable-cell');
        // Prevent editing if the cell has 'media' as its field or is not editable
        if (!cell || cell.classList.contains('editing') || cell.dataset.field === 'media') return;

        const isProfessorTable = cell.closest('#professorStudentTable');
        const isStudentTable = cell.closest('#studentTable');

        // Prevent editing based on user role and table
        if (currentUser.role === 'professor' && isStudentTable) return; // Professors can only edit their assigned students/disciplines via professor table
        if ((currentUser.role === 'admin' || currentUser.role === 'coordenador') && isProfessorTable) return; // Admins/Coordinators can edit via student table
        if (currentUser.role === 'aluno') return; // Students cannot edit

         // Additional check for professor: ensure the selected cell's discipline/class is assigned to the professor
        if (currentUser.role === 'professor' && isProfessorTable) {
            const disciplineName = cell.dataset.disciplineName;
            const classMatch = currentUser.assignments.some(assignment =>
                assignment.discipline === disciplineName &&
                assignment.classes.includes(document.getElementById('professorClassSelect').value) // Check against the selected class in the professor view
            );
            if (!classMatch) {
                 alert('Você não está atribuído a esta disciplina nesta turma.'); // Optional: provide feedback
                return; // Prevent editing if not assigned
            }
        }


        cell.classList.add('editing');
        const currentValue = cell.querySelector('span') ? cell.querySelector('span').textContent.trim() : cell.textContent.trim(); // Get value from span if exists
        const studentId = cell.dataset.studentId;
        const disciplineName = cell.dataset.disciplineName;
        const unitNumber = parseInt(cell.dataset.unitNumber);
        const field = cell.dataset.field;
        const inputType = cell.dataset.type;
        const options = cell.dataset.options ? cell.dataset.options.split(',') : [];
        let inputElement;
        if (inputType === 'select') {
            inputElement = document.createElement('select');
            options.forEach(optionValue => {
                const option = document.createElement('option');
                option.value = optionValue;
                // For numerical grades, display the number with comma. For mentions/situations, display the full text.
                if (['test1', 'test2', 'eval1'].includes(field)) {
                    option.textContent = String(optionValue).replace('.', ','); // Display with comma for decimals
                } else {
                    option.textContent = optionValue;
                }

                if (currentValue.replace(',', '.') == optionValue || (currentValue === '-' && optionValue === '')) { // Compare after replacing comma with dot for numerical values
                    option.selected = true;
                }
                inputElement.appendChild(option);
            });
        } else if (inputType === 'text') {
            inputElement = document.createElement('input'); inputElement.type = 'text'; inputElement.value = currentValue;
        } else { cell.classList.remove('editing'); return; }
        cell.innerHTML = ''; cell.appendChild(inputElement); inputElement.focus();
        inputElement.addEventListener('blur', saveEditableCell);
        inputElement.addEventListener('keypress', function(e) { if (e.key === 'Enter') saveEditableCell(e); });
    }

    function saveEditableCell(event) {
        const inputElement = event.target;
        const cell = inputElement.closest('.editable-cell');
        if (!cell || !cell.classList.contains('editing') || cell.dataset.field === 'media') return; // Prevent saving for media field
        let newValue = inputElement.value.trim();
        const studentId = cell.dataset.studentId;
        const disciplineName = cell.dataset.disciplineName;
        const unitNumber = parseInt(cell.dataset.unitNumber);
        const field = cell.dataset.field;
        const student = students.find(s => s.id === studentId);

        if (student) {
            let disciplineEntry = student.disciplines.find(d => d.discipline === disciplineName && d.unit === unitNumber);
            if (!disciplineEntry) {
                // Initialize all numerical fields to empty string, and mention/situation to default
                disciplineEntry = {
                    discipline: disciplineName,
                    unit: unitNumber,
                    test1: '', test2: '', eval1: '', media: '', // Initialize media field
                    finalGrade: '', situation: 'Pendente', observation: ''
                };
                student.disciplines.push(disciplineEntry);
            }
            // Parse numerical values if applicable (replace comma with dot for parseFloat)
            if (['test1', 'test2', 'eval1'].includes(field)) {
                newValue = newValue === '' ? '' : parseFloat(newValue.replace(',', '.')); // Store empty string for empty input, or float for numbers
                if (isNaN(newValue) && newValue !== '') { // If not a number and not empty, revert
                    newValue = parseFloat(inputElement.defaultValue.replace(',', '.')); // Revert to parsed default
                    alert('Por favor, insira um número válido para a nota.');
                }
            }

            disciplineEntry[field] = newValue;

            // Recalculate media after any relevant field change
            const t1 = parseFloat(disciplineEntry.test1) || 0;
            const t2 = parseFloat(disciplineEntry.test2) || 0;
            const ev1 = parseFloat(disciplineEntry.eval1) || 0;
            disciplineEntry.media = ((t1 + t2 + ev1) / 3).toFixed(2); // Calculate and store media, rounded to 2 decimal places

            let displayValue = newValue;

            if (field === 'media' && displayValue !== undefined && displayValue !== null && displayValue !== '') {
                displayValue = parseFloat(displayValue).toFixed(2).replace('.', ',');
            } else if (['test1', 'test2', 'eval1'].includes(field) && displayValue !== undefined && displayValue !== null && displayValue !== '') {
                displayValue = String(displayValue).replace('.', ',');
            }
            else if (displayValue === '' || displayValue === null || displayValue === undefined) {
                 displayValue = (field === 'observation' || field === 'finalGrade' || field === 'situation') ? '' : '-'; // Display '-' for empty numerical/evaluation, '' for observation
            }

            cell.innerHTML = `<span>${displayValue}</span>`;
            saveData(); // Save data after editing a cell
            // Re-render table to ensure media column updates if relevant fields changed
            renderStudentTable(students);
            if (currentUser && currentUser.role === 'professor') loadProfessorTable();
            if (currentUser && currentUser.role === 'aluno' && currentUser.studentId === student.id) showStudentBulletin();

        } else {
            console.error('Erro: Aluno não encontrado para edição.'); cell.innerHTML = `<span>${inputElement.defaultValue.replace('.', ',')}</span>`; // Revert if error, display with comma
        }
        cell.classList.remove('editing');
    }

    // Modified populateProfessorSelects to use the new assignments structure
    function populateProfessorSelects(user) {
        const disciplineSelect = document.getElementById('professorDisciplineSelect');
        const classSelect = document.getElementById('professorClassSelect');
        const unitSelect = document.getElementById('professorUnitSelect');

        disciplineSelect.innerHTML = '<option value="">Selecione a Disciplina</option>';
        classSelect.innerHTML = '<option value="">Selecione a Turma</option>';
         unitSelect.value = ''; // Reset unit selection

        if (user && user.assignments) {
            // Populate discipline select based on assigned disciplines
            const uniqueDisciplines = [...new Set(user.assignments.map(assignment => assignment.discipline))].sort();
            uniqueDisciplines.forEach(discipline => { const option = document.createElement('option'); option.value = discipline; option.textContent = discipline; disciplineSelect.appendChild(option); });

            // Add event listener to discipline select to populate class select
            disciplineSelect.removeEventListener('change', updateProfessorClassSelect);
            disciplineSelect.addEventListener('change', updateProfessorClassSelect);

            // Initial population of class select based on the default (or first) selected discipline
            updateProfessorClassSelect();

        }

        disciplineSelect.removeEventListener('change', loadProfessorTable);
        classSelect.removeEventListener('change', loadProfessorTable);
        unitSelect.removeEventListener('change', loadProfessorTable);

        disciplineSelect.addEventListener('change', loadProfessorTable);
        classSelect.addEventListener('change', loadProfessorTable);
        unitSelect.addEventListener('change', loadProfessorTable);
    }

    // New function to update the class select based on the selected discipline for the professor
    function updateProfessorClassSelect() {
        const disciplineSelect = document.getElementById('professorDisciplineSelect');
        const classSelect = document.getElementById('professorClassSelect');
        const selectedDiscipline = disciplineSelect.value;

        // Also update notes section selects
        const notesClassSelect = document.getElementById('notesClassSelect'); // Make sure this is defined
        const notesStudentSelect = document.getElementById('notesStudentSelect'); // Make sure this is defined

        notesClassSelect.innerHTML = '<option value="">Selecione a Turma</option>';
        notesClassSelect.disabled = true;
        notesStudentSelect.innerHTML = '<option value="">Selecione o Aluno</option>';
        notesStudentSelect.disabled = true;
        document.getElementById('professorNoteContent').value = '';
        document.getElementById('existingProfessorNotes').innerHTML = '<p class="no-notes" style="text-align: center; font-style: italic;">Selecione aluno, disciplina e unidade para ver ou adicionar anotações.</p>';

        classSelect.innerHTML = '<option value="">Selecione a Turma</option>';
        classSelect.disabled = true;

        if (currentUser && currentUser.assignments && selectedDiscipline) {
            const assignment = currentUser.assignments.find(a => a.discipline === selectedDiscipline);
            if (assignment && assignment.classes.length > 0) {
                assignment.classes.sort().forEach(className => {
                    const option = document.createElement('option');
                    option.value = className;
                    option.textContent = className;
                    classSelect.appendChild(option);
                    // Also add to notesClassSelect
                    const notesOption = document.createElement('option');
                    notesOption.value = className;
                    notesOption.textContent = className;
                    notesClassSelect.appendChild(notesOption);
                });
                notesClassSelect.disabled = false;
                classSelect.disabled = false;
            }
        }
         // Also clear the table and show message when discipline changes
        document.querySelector('#professorStudentTable tbody').innerHTML = '';
        document.getElementById('professorNoStudentsMessage').classList.remove('hidden');
         document.querySelector('#professorStudentTable thead').classList.add('hidden'); // Hide table header
    }


     // Modified loadProfessorTable to use the new assignments structure and selected class
    function loadProfessorTable() {
        const selectedDiscipline = document.getElementById('professorDisciplineSelect').value;
        const selectedClass = document.getElementById('professorClassSelect').value;
        const selectedUnit = document.getElementById('professorUnitSelect').value;

        // Check if the professor is assigned to this discipline in this class
        const isAssigned = currentUser && currentUser.assignments &&
                           currentUser.assignments.some(assignment =>
                               assignment.discipline === selectedDiscipline &&
                               assignment.classes.includes(selectedClass)
                           );

        if (selectedDiscipline && selectedClass && selectedUnit && isAssigned) {
            const studentsToDisplay = students.filter(student => student.class === selectedClass);
            renderProfessorTable(studentsToDisplay, selectedDiscipline, selectedClass, parseInt(selectedUnit));
        } else {
            document.querySelector('#professorStudentTable tbody').innerHTML = '';
            document.getElementById('professorNoStudentsMessage').classList.remove('hidden');
             document.querySelector('#professorStudentTable thead').classList.add('hidden'); // Hide table header
        }
    }


    function addStudent() {
        const studentNameInput = document.getElementById('studentName');
        const studentMatriculaInput = document.getElementById('studentMatricula');
        const classSelect = document.getElementById('class');
        const studentShiftSelect = document.getElementById('studentShift'); // Get the new shift select

        const name = studentNameInput.value.trim();
        const matricula = studentMatriculaInput.value.trim();
        const className = classSelect.value;
        const studentShift = studentShiftSelect.value; // Get the selected shift

        const classInfo = getClassInfo(className); // Still used for course

        if (!name || !matricula || !className || !studentShift) { // Validate studentShift now
            alert('Por favor, preencha o Nome do Aluno, a Matrícula, selecione a Turma e o Turno.');
            return;
        }

        // Check if matricula already exists
        if (students.some(s => s.matricula && s.matricula.toLowerCase() === matricula.toLowerCase())) {
            alert('Matrícula já existe. Por favor, insira uma matrícula única.');
            return;
        }

        // Generate a simple unique ID (timestamp + random number)
        const newStudentId = 's' + Date.now() + Math.floor(Math.random() * 1000);

        // Use studentShift for 'unit' field now (This means 'unit' will store "Manhã" or "Tarde" for student's shift)
        const newStudent = { id: newStudentId, matricula: matricula, name: name, course: classInfo.course, class: className, unit: studentShift, disciplines: [], professorNotes: [] };
        students.push(newStudent);
        studentNameInput.value = '';
        studentMatriculaInput.value = '';
        classSelect.value = '';
        studentShiftSelect.value = ''; // Clear shift select
        saveData();
        renderStudentTable(students);
        populateClassSelect(document.getElementById('disciplineClassSelect')); populateStudentSelectForDiscipline();
        populateClassSelect(document.getElementById('printClassSelect')); populateStudentPrintSelect();
        if (currentUser && currentUser.role === 'professor') loadProfessorTable();
        alert('Aluno adicionado com sucesso!');
    }


    // No longer need updateStudentShiftDisplay since it's a direct input
    // function updateStudentShiftDisplay() {
    //     const classSelect = document.getElementById('class');
    //     const studentShiftDisplay = document.getElementById('studentShiftDisplay');
    //     const selectedClass = classSelect.value;
    //     if (selectedClass) {
    //         const classInfo = getClassInfo(selectedClass);
    //         studentShiftDisplay.textContent = classInfo.unit;
    //     } else {
    //         studentShiftDisplay.textContent = '-';
    //     }
    // }


    // Event listeners for score inputs to calculate media dynamically
    document.getElementById('test1').addEventListener('change', calculateAndDisplayMedia);
    document.getElementById('test2').addEventListener('change', calculateAndDisplayMedia);
    document.getElementById('evaluation1').addEventListener('change', calculateAndDisplayMedia);

    function calculateAndDisplayMedia() {
        const test1 = parseFloat(document.getElementById('test1').value.replace(',', '.')); // Parse with dot
        const test2 = parseFloat(document.getElementById('test2').value.replace(',', '.')); // Parse with dot
        const eval1 = parseFloat(document.getElementById('evaluation1').value.replace(',', '.')); // Parse with dot

        // Only calculate if all three scores are valid numbers
        if (!isNaN(test1) && !isNaN(test2) && !isNaN(eval1)) {
            const media = ((test1 + test2 + eval1) / 3).toFixed(2);
            document.getElementById('mediaDisplay').textContent = media.replace('.', ','); // Display with comma
        } else {
            document.getElementById('mediaDisplay').textContent = '-'; // Display hyphen if any score is invalid
        }
    }


    function addDiscipline() {
        const disciplineClassSelect = document.getElementById('disciplineClassSelect');
        const studentSelect = document.getElementById('studentSelect');
        const disciplineSelect = document.getElementById('disciplineSelect');
        const unitSelectDiscipline = document.getElementById('unitSelect');
        const test1Select = document.getElementById('test1');
        const test2Select = document.getElementById('test2');
        const evaluation1Select = document.getElementById('evaluation1');
        const finalGradeSelect = document.getElementById('finalGrade');
        const observationInput = document.getElementById('observationInput');

        const selectedClass = disciplineClassSelect.value;
        const studentId = studentSelect.value;
        const disciplineName = disciplineSelect.value;
        const unitNumber = parseInt(unitSelectDiscipline.value);
        const test1 = test1Select.value; // Get string value
        const test2 = test2Select.value; // Get string value
        const eval1 = evaluation1Select.value; // Get string value
        const finalGrade = finalGradeSelect.value;
        const observation = observationInput.value.trim();

        // Validate if all required fields are filled and numerical inputs are not empty strings
        if (!selectedClass || !studentId || !disciplineName || !unitNumber || test1 === '' || test2 === '' || eval1 === '' || !finalGrade) {
            alert('Por favor, preencha a Turma, o Aluno e preencha todos os campos da disciplina (Notas de Teste, Avaliação, Menção Final e Unidade).');
            return;
        }
        // Parse numerical values after validation (replace comma with dot)
        const parsedTest1 = parseFloat(test1.replace(',', '.'));
        const parsedTest2 = parseFloat(test2.replace(',', '.'));
        const parsedEval1 = parseFloat(eval1.replace(',', '.'));

        const student = students.find(s => s.id === studentId);
        if (student) {
            if (student.class !== selectedClass) { alert('Erro: O aluno selecionado não pertence à turma escolhida.'); return; }
            const existingDiscipline = student.disciplines.find(d => d.discipline === disciplineName && d.unit === unitNumber);
            if (existingDiscipline) { alert(`A disciplina "${disciplineName}" para a Unidade ${unitNumber} já existe para este aluno.`); return; }

            let situation = 'Pendente'; // Default
            if (finalGrade === 'Aprovado') situation = 'Aprovado';
            else if (finalGrade === 'Reprovado') situation = 'Reprovado';
            else if (finalGrade === 'Recuperacao') situation = 'Recuperação'; // New situation for Recuperacao

            const media = ((parsedTest1 + parsedTest2 + parsedEval1) / 3).toFixed(2); // Calculate media

            const newDiscipline = {
                discipline: disciplineName,
                unit: unitNumber,
                test1: parsedTest1,
                test2: parsedTest2,
                eval1: parsedEval1,
                media: media, // Store calculated media
                finalGrade: finalGrade,
                situation: situation,
                observation: observation
            };
            student.disciplines.push(newDiscipline);
            disciplineClassSelect.value = '';
            populateStudentSelectForDiscipline();
            disciplineSelect.value = '';
            unitSelectDiscipline.value = '';
            test1Select.value = ''; // Reset to empty string
            test2Select.value = ''; // Reset to empty string
            evaluation1Select.value = ''; // Reset to empty string
            finalGradeSelect.value = '';
            observationInput.value = '';
            document.getElementById('mediaDisplay').textContent = '-'; // Reset media display
            saveData(); // Save data after adding a discipline
            renderStudentTable(students);
            if (currentUser && currentUser.role === 'professor') loadProfessorTable();
            if (currentUser && currentUser.role === 'aluno' && currentUser.studentId === student.id) showStudentBulletin();
            alert('Disciplina adicionada com sucesso!');
        } else { alert('Aluno não encontrado.'); }
    }

    function populateStudentSelectForDiscipline(className = '') {
        const studentSelect = document.getElementById('studentSelect'); studentSelect.innerHTML = '';
        const defaultOption = document.createElement('option'); defaultOption.value = ""; defaultOption.textContent = className ? "Carregando alunos..." : "Selecione a Turma Primeiro";
        studentSelect.appendChild(defaultOption); studentSelect.disabled = true;
        setTimeout(() => {
            const studentsToDisplay = students.filter(student => student.class === className); // Filter by class
            studentSelect.innerHTML = ''; // Clear options again after filter

            const fragment = document.createDocumentFragment();
            if (studentsToDisplay.length > 0) {
                const selectStudentOption = document.createElement('option'); selectStudentOption.value = ""; selectStudentOption.textContent = "Selecione o Aluno"; fragment.appendChild(selectStudentOption);
                studentsToDisplay.forEach(student => { const option = document.createElement('option'); option.value = student.id; option.textContent = `${student.name} (${student.matricula})`; fragment.appendChild(option); }); // Display matricula in student select
                studentSelect.disabled = false;
            } else {
                const noStudentsOption = document.createElement('option'); noStudentsOption.value = ""; noStudentsOption.textContent = "Nenhum aluno encontrado para a Turma selecionada"; fragment.appendChild(noStudentsOption); studentSelect.disabled = true;
            }
            studentSelect.appendChild(fragment);
        }, 50);
    }

    function populateStudentPrintSelect(className = '') {
        const studentSelect = document.getElementById('studentSelectPrint'); studentSelect.innerHTML = '';
        const defaultOption = document.createElement('option'); defaultOption.value = ""; defaultOption.textContent = className ? "Carregando alunos..." : "Selecione a Turma Primeiro";
        studentSelect.appendChild(defaultOption); studentSelect.disabled = true;
        setTimeout(() => {
            const studentsToDisplay = className ? students.filter(student => student.class === className) : []; studentSelect.innerHTML = '';
            const fragment = document.createDocumentFragment();
            if (studentsToDisplay.length > 0) {
                const selectStudentOption = document.createElement('option'); selectStudentOption.value = ""; selectStudentOption.textContent = "Selecione o Aluno"; fragment.appendChild(selectStudentOption);
                studentsToDisplay.forEach(student => { const option = document.createElement('option'); option.value = student.id; option.textContent = `${student.name} (${student.matricula}) - ${student.unit}`; fragment.appendChild(option); }); // Display matricula
                studentSelect.disabled = false;
            } else {
                const noStudentsOption = document.createElement('option'); noStudentsOption.value = ""; noStudentsOption.textContent = "Selecione a Turma Primeiro"; fragment.appendChild(noStudentsOption); studentSelect.disabled = true;
            }
            studentSelect.appendChild(fragment);
        }, 50);
    }

    function populateClassSelect(selectElement) {
        selectElement.innerHTML = '<option value="">Selecione a Turma</option>';
        const optgroups = {
            'Educação Infantil': [],
            'Fundamental 1': [],
            'Fundamental 2': [],
            'Ensino Médio': []
        };

        for (const className in classInfoMap) {
            const category = classInfoMap[className].course;
            if (optgroups[category]) {
                optgroups[category].push(className);
            }
        }

        for (const category in optgroups) {
            if (optgroups[category].length > 0) {
                const optgroup = document.createElement('optgroup');
                optgroup.label = category;
                optgroups[category].sort().forEach(className => {
                    const option = document.createElement('option');
                    option.value = className;
                    option.textContent = className;
                    optgroup.appendChild(option);
                });
                selectElement.appendChild(optgroup);
            }
        }
    }

    // Function to populate the Discipline Select
    function populateDisciplineSelect(selectElement) {
        selectElement.innerHTML = '<option value="">Selecione a Disciplina</option>';
        allDisciplines.forEach(discipline => {
            const option = document.createElement('option');
            option.value = discipline;
            option.textContent = discipline;
            selectElement.appendChild(option);
        });
    }

    function printAllReports() {
        // This function will now print ALL students from ALL classes, respecting unit and report type filters
        const selectedUnits = Array.from(document.querySelectorAll('#printControls .unitCheckbox:checked')).map(cb => parseInt(cb.value));
        const reportType = document.querySelector('#printControls input[name="reportType"]:checked').value;

        if (selectedUnits.length === 0) {
            alert('Por favor, selecione pelo menos uma unidade para imprimir.');
            return;
        }

        let allBulletinsHTML = '';
        students.forEach(student => {
            allBulletinsHTML += generateBulletinHTML(student, selectedUnits, reportType, true); // Pass true to include notes
        });

        if (allBulletinsHTML === '') {
            alert('Nenhum dado de boletim encontrado para os filtros selecionados.');
            return;
        }
        openPrintWindow(allBulletinsHTML, "Boletins de Todos os Alunos");
    }


    function printStudentReport() {
        const printClassSelect = document.getElementById('printClassSelect');
        const studentSelect = document.getElementById('studentSelectPrint');
        const selectedUnits = Array.from(document.querySelectorAll('#printControls .unitCheckbox:checked')).map(cb => parseInt(cb.value));
        const reportType = document.querySelector('#printControls input[name="reportType"]:checked').value;
        const studentId = studentSelect.value;

        if (!studentId) { alert('Por favor, selecione o Aluno para imprimir.'); return; }
        if (selectedUnits.length === 0) { alert('Por favor, selecione pelo menos uma unidade.'); return;}

        const student = students.find(s => s.id === studentId);
        if (!student) { alert('Aluno não encontrado para impressão.'); return; }

        const bulletinHTML = generateBulletinHTML(student, selectedUnits, reportType, true); // Pass true to include notes
        openPrintWindow(bulletinHTML, `Boletim de ${student.name}`);
    }

    // NOVA FUNÇÃO para imprimir boletins da turma
    function printClassReports() {
        const printClassSelect = document.getElementById('printClassSelect');
        const selectedClass = printClassSelect.value;
        const selectedUnits = Array.from(document.querySelectorAll('#printControls .unitCheckbox:checked')).map(cb => parseInt(cb.value));
        const reportType = document.querySelector('#printControls input[name="reportType"]:checked').value;

        if (!selectedClass) {
            alert('Por favor, selecione a Turma para imprimir.');
            return;
        }
        if (selectedUnits.length === 0) {
            alert('Por favor, selecione pelo menos uma unidade para imprimir.');
            return;
        }

        const studentsInClass = students.filter(student => student.class === selectedClass);

        if (studentsInClass.length === 0) {
            alert(`Nenhum aluno encontrado na turma ${selectedClass}.`);
            return;
        }

        let classBulletinsHTML = '';
        studentsInClass.forEach(student => {
            classBulletinsHTML += generateBulletinHTML(student, selectedUnits, reportType, true); // Pass true to include notes
        });

        if (classBulletinsHTML === '') {
            alert(`Nenhum dado de boletim encontrado para a turma ${selectedClass} com os filtros selecionados.`);
            return;
        }
        openPrintWindow(classBulletinsHTML, `Boletins da Turma ${selectedClass}`);
    }


    // MODIFICADA: generateBulletinHTML para incluir anotações
    function generateBulletinHTML(student, unitsToInclude, reportType = 'full', includeProfessorNotes = false) {
        let bulletinHTML = `<div class="student-report"><div class="bulletin-header"><p class="line1"><strong>Escola Academia Primeiros Passos</strong> - 2025</p><p class="line2">Boletim Escolar - APP</p><p class="line3"><strong>Aluno:</strong> ${student.name} (${student.matricula}) - <strong>Turma:</strong> ${student.class} - <strong>Turno:</strong> ${student.unit} - <strong>Curso:</strong> ${student.course}</p></div><table class="bulletin-table"><thead><tr><th>Disciplina</th><th>Unidade</th>${reportType === 'full' ? '<th>Teste 1</th><th>Teste 2</th><th>Avaliação</th><th>Média</th>' : ''}<th>Menção Final</th><th>Situação</th><th>Observações</th></tr></thead><tbody>`; // Updated table header: added Matrícula and Média
        const disciplinesToPrint = student.disciplines.filter(d => unitsToInclude.includes(d.unit)).sort((a, b) => { if (a.unit !== b.unit) return a.unit - b.unit; return a.discipline.localeCompare(b.discipline); });
        if (disciplinesToPrint.length === 0) {
            const colspan = reportType === 'full' ? 9 : 5; // Updated colspan: 9 for full (Disciplina, Unidade, Teste 1, Teste 2, Avaliação, Média, Menção Final, Situação, Observações = 9), 5 for summary (Disciplina, Unidade, Menção Final, Situação, Observações = 5)
            bulletinHTML += `<tr><td colspan="${colspan}">Nenhuma disciplina ou nota encontrada para as unidades selecionadas.</td></tr>`;
        } else {
            disciplinesToPrint.forEach(discipline => {
                const test1Display = discipline.test1 !== undefined && discipline.test1 !== null ? String(discipline.test1).replace('.', ',') : '-'; // Display with comma
                const test2Display = discipline.test2 !== undefined && discipline.test2 !== null ? String(discipline.test2).replace('.', ',') : '-'; // Display with comma
                const eval1Display = discipline.eval1 !== undefined && discipline.eval1 !== null ? String(discipline.eval1).replace('.', ',') : '-'; // Display with comma
                const mediaDisplay = discipline.media !== undefined && discipline.media !== null ? parseFloat(discipline.media).toFixed(2).replace('.', ',') : '-'; // Display media rounded with comma

                bulletinHTML += `<tr><td>${discipline.discipline}</td><td>${discipline.unit}</td>${reportType === 'full' ? `<td>${test1Display}</td><td>${test2Display}</td><td>${eval1Display}</td><td>${mediaDisplay}</td>` : ''}<td>${discipline.finalGrade || '-'}</td><td>${discipline.situation || '-'}</td><td>${discipline.observation || ''}</td></tr>`;
            });
        }
        bulletinHTML += `</tbody></table>`;

        // NEW: Add professor notes to the print output if requested
        if (includeProfessorNotes && student.professorNotes && student.professorNotes.length > 0) {
            const notesForPrint = student.professorNotes.filter(note => unitsToInclude.includes(note.unit)).sort((a, b) => {
                // Sort by date (descending), then by discipline, then by professor name
                const dateA = new Date(a.date);
                const dateB = new Date(b.date);
                if (dateA.getTime() !== dateB.getTime()) return dateB.getTime() - dateA.getTime();
                if (a.discipline !== b.discipline) return a.discipline.localeCompare(b.discipline);
                return a.professorName.localeCompare(b.professorName);
            });

            if (notesForPrint.length > 0) {
                bulletinHTML += `<div class="professor-notes-print"><h4>Anotações dos Professores:</h4>`;
                notesForPrint.forEach(note => {
                    const noteItem = document.createElement('div');
                    noteItem.classList.add('professor-note-item');
                    noteItem.innerHTML = `
                        <p><strong>Disciplina:</strong> ${note.discipline}, <strong>Unidade:</strong> ${note.unit}</p>
                        <p><strong>Anotação:</strong> ${note.content}</p>
                        <span class="note-meta">Feita por: ${note.professorName} em ${new Date(note.date).toLocaleDateString()}</span>
                    `;
                    bulletinHTML += noteItem.outerHTML; // Append the HTML of the created element
                });
                bulletinHTML += `</div>`;
            }
        }

        bulletinHTML += `</div>`; // Close student-report div
        return bulletinHTML;
    }

    // Helper para abrir janela de impressão
    function openPrintWindow(contentHTML, title) {
        const printWindow = window.open('', '_blank');
        printWindow.document.open();
        printWindow.document.write(`
            <!DOCTYPE html>
            <html><head><title>${title}</title>
                <style>
                    body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; margin: 1.5cm; font-size: 10pt; }
                    .student-report { page-break-inside: avoid; page-break-after: always; margin-bottom: 0; padding: 10px 0;}
                    .student-report:last-child { page-break-after: avoid; }
                    .bulletin-header { text-align: center; margin-bottom: 20px; padding-bottom: 15px; border-bottom: 2px solid #A52A2A; }
                    .bulletin-header p { margin: 5px 0; font-size: 11pt; color: #A52A2A; } .bulletin-header p strong { font-weight: bold; }
                    .bulletin-header .line1 { font-size: 18pt; font-weight: bold; margin-bottom: 8px; }
                    .bulletin-header .line2 { font-size: 14pt; margin-bottom: 8px; }
                    .bulletin-header .line3 { font-size: 11pt; margin-top: 8px; margin-bottom: 0; }
                    .bulletin-table { width: 100%; border-collapse: collapse; margin-top: 15px; }
                    .bulletin-table th, .bulletin-table td { border: 1px solid #A52A2A; padding: 8px; text-align: center; font-size: 9pt; }
                    .bulletin-table th { background-color: yellow !important; color: #A52A2A !important; font-weight: bold; }
                    .bulletin-table td:first-child { text-align: left; } .bulletin-table td:last-child { text-align: left; }
                    @page { size: A4; margin: 1.5cm; }
                    /* New print styles for professor notes */
                    .professor-notes-print { margin-top: 25px; padding-top: 15px; border-top: 1px solid yellow; }
                    .professor-notes-print h4 { font-size: 12pt; margin-bottom: 10px; color: #A52A2A; }
                    .professor-note-item { border: 1px solid yellow; padding: 8px; margin-bottom: 8px; background-color: white; page-break-inside: avoid; }
                    .professor-note-item p { margin: 0; line-height: 1.4; }
                    .professor-note-item strong { font-weight: bold; }
                    .professor-note-item span { font-size: 9pt; color: #A52A2A; display: block; margin-top: 5px; }
                </style>
            </head><body>${contentHTML}</body></html>`);
        printWindow.document.close();
        printWindow.print();
    }


    // Modified showAddProfessorForm to populate the new assignment structure UI
    function showAddProfessorForm() {
        populateProfessorAssignmentCheckboxes(document.getElementById('newProfessorAssignments'));
        document.getElementById('addProfessorModal').classList.remove('hidden');
    }

    function closeAddProfessorModal() {
        document.getElementById('addProfessorModal').classList.add('hidden');
        document.getElementById('newProfessorNameInput').value = '';
        document.getElementById('newProfessorUsernameInput').value = '';
        document.getElementById('newProfessorPasswordInput').value = '';
        document.getElementById('newProfessorAssignments').innerHTML = ''; // Clear the assignment checkboxes
    }

    // Modified saveProfessor to capture the new assignment structure
    function saveProfessor() {
        const name = document.getElementById('newProfessorNameInput').value.trim();
        const username = document.getElementById('newProfessorUsernameInput').value.trim();
        const password = document.getElementById('newProfessorPasswordInput').value;

        if (!name || !username || !password) { alert('Por favor, preencha Nome, Usuário e Senha para o professor.'); return; }
        if (users.some(user => user.username === username)) { alert('Nome de usuário já existe. Por favor, escolha outro.'); return; }

        // Capture assignments from the new UI structure
        const assignments = [];
        document.querySelectorAll('#newProfessorAssignments .discipline-assignment').forEach(disciplineDiv => {
            const discipline = disciplineDiv.dataset.discipline;
            const selectedClasses = Array.from(disciplineDiv.querySelectorAll('.class-checkboxes input[type="checkbox"]:checked')).map(cb => cb.value);
            if (selectedClasses.length > 0) {
                assignments.push({ discipline: discipline, classes: selectedClasses });
            }
        });

        users.push({ username: username, password: password, role: 'professor', name: name, assignments: assignments });
        saveData(); // Save data after adding a professor
        closeAddProfessorModal();
        renderUsersTable(users);
        alert('Professor adicionado com sucesso!');
    }

    function showAddCoordenadorForm() { document.getElementById('addCoordinatorModal').classList.remove('hidden'); }
    function closeAddCoordenadorModal() { document.getElementById('addCoordinatorModal').classList.add('hidden'); document.getElementById('newCoordinatorNameInput').value = ''; document.getElementById('newCoordinatorUsernameInput').value = ''; document.getElementById('newCoordinatorPasswordInput').value = ''; }
    function saveCoordinator() {
        const name = document.getElementById('newCoordinatorNameInput').value.trim(); const username = document.getElementById('newCoordinatorUsernameInput').value.trim(); const password = document.getElementById('newCoordinatorPasswordInput').value;
        if (!name || !username || !password) { alert('Por favor, preencha Nome, Usuário e Senha para o coordenador.'); return; }
        if (users.some(user => user.username === username)) { alert('Nome de usuário já existe. Por favor, escolha outro.'); return; }
        users.push({ username: username, password: password, role: 'coordenador', name: name, assignments: [] }); // Coordinators have empty assignments
        saveData(); // Save data after adding a coordinator
        closeAddCoordenadorModal(); renderUsersTable(users); alert('Coordenador adicionado com sucesso!');
    }
    function showManageUsersSection() { showSection(manageUsersSection); renderUsersTable(users); }

    // Modified editUser to populate the new assignment structure UI
    function editUser(username) {
        const user = users.find(u => u.username === username); if (!user) { alert('Usuário não encontrado para edição.'); return; }
        document.getElementById('editUserModalTitle').textContent = `Editar Usuário: ${user.name}`; document.getElementById('editUserOriginalUsername').value = user.username; document.getElementById('editUserRole').value = user.role;
        document.getElementById('editUserNameInput').value = user.name; document.getElementById('editUserUsernameInput').value = user.username; document.getElementById('editUserPasswordInput').value = '';

        const professorAssignmentsDiv = document.getElementById('editProfessorAssignments');
        if (user.role === 'professor') {
            professorAssignmentsDiv.classList.remove('hidden');
            populateProfessorAssignmentCheckboxes(professorAssignmentsDiv, user.assignments); // Populate with existing assignments
        } else {
            professorAssignmentsDiv.classList.add('hidden');
             professorAssignmentsDiv.innerHTML = ''; // Clear assignments if not a professor
        }

         // Hide assignments for student users in the edit modal (redundant with above but keeps logic clear)
        if (user.role === 'aluno') { professorAssignmentsDiv.classList.add('hidden'); professorAssignmentsDiv.innerHTML = ''; }

        document.getElementById('editUserModal').classList.remove('hidden');
    }

    function closeEditUserModal() {
        document.getElementById('editUserModal').classList.add('hidden');
        document.getElementById('editUserOriginalUsername').value = '';
        document.getElementById('editUserRole').value = '';
        document.getElementById('editUserNameInput').value = '';
        document.getElementById('editUserUsernameInput').value = '';
        document.getElementById('editUserPasswordInput').value = '';
        document.getElementById('editProfessorAssignments').innerHTML = ''; // Clear assignment checkboxes
    }

    // Modified updateUser to save the new assignment structure
    function updateUser() {
        const originalUsername = document.getElementById('editUserOriginalUsername').value;
        const userRole = document.getElementById('editUserRole').value;
        const newName = document.getElementById('editUserNameInput').value.trim();
        const newUsername = document.getElementById('editUserUsernameInput').value.trim();
        const newPassword = document.getElementById('editUserPasswordInput').value;

        if (!newName || !newUsername) { alert('Nome e Usuário não podem ser vazios.'); return; }
        if (newUsername !== originalUsername && users.some(user => user.username === newUsername)) { alert('Nome de usuário já existe. Por favor, escolha outro.'); return; }

        const userIndex = users.findIndex(u => u.username === originalUsername); if (userIndex === -1) { alert('Erro: Usuário original não encontrado.'); return; }

        users[userIndex].name = newName; users[userIndex].username = newUsername; if (newPassword) users[userIndex].password = newPassword;

        // Update assignments based on the new UI structure if the user is a professor
        if (userRole === 'professor') {
            const updatedAssignments = [];
            document.querySelectorAll('#editProfessorAssignments .discipline-assignment').forEach(disciplineDiv => {
                const discipline = disciplineDiv.dataset.discipline;
                const selectedClasses = Array.from(disciplineDiv.querySelectorAll('.class-checkboxes input[type="checkbox"]:checked')).map(cb => cb.value);
                 if (selectedClasses.length > 0) {
                    updatedAssignments.push({ discipline: discipline, classes: selectedClasses });
                 }
            });
             users[userIndex].assignments = updatedAssignments;
        }
         // For other roles, assignments remain empty or unchanged

        saveData(); // Save data after updating a user
        closeEditUserModal();
        renderUsersTable(users);

        if (currentUser && currentUser.username === originalUsername) {
            currentUser = users[userIndex];
            // Update studentId link if username changed for an aluno user
            if (currentUser.role === 'aluno') {
                 // Try to relink student to the new username (matricula)
                const student = students.find(s => s.matricula && s.matricula.trim().toLowerCase() === currentUser.username.trim().toLowerCase());
                 if (student) {
                    currentUser.studentId = student.id;
                 } else {
                     console.warn('Could not relink student data after username update for user:', currentUser.username);
                      // Decide how to handle this - maybe revert the username change or show an error
                 }
                 showStudentBulletin(); // Refresh bulletin for the student
            } else if (currentUser.role === 'admin' || currentUser.role === 'coordenador') {
                showStudentManagementSection(); // Refresh student management for admin/coordinator
            } else if (currentUser.role === 'professor') {
                 showProfessorSection(currentUser); // Refresh professor section for professor
            }
        }
        alert('Usuário atualizado com sucesso!');
    }

    function deleteUser(username) {
        if (username === 'administrador') { alert('Não é possível excluir o usuário administrador principal.'); return; }
        if (currentUser && currentUser.username === username) { alert('Você não pode excluir seu próprio usuário.'); return; }
        // Removed the explicit check preventing deletion of 'aluno' users
        if (confirm(`Tem certeza que deseja excluir o usuário "${username}"? Esta ação não pode ser desfeita."`)) {
            const initialUserCount = users.length; users = users.filter(user => user.username !== username);
            if (users.length < initialUserCount) {
                 saveData(); // Save data after deleting a user
                 renderUsersTable(users);
                 alert('Usuário excluído com sucesso.');
                 // If the deleted user was the current user, log out
                 if (currentUser && currentUser.username === username) {
                     logout();
                 }
             } else { alert('Erro ao excluir usuário: Usuário não encontrado.'); }
        }
    }
    function searchStudent() {
        const searchTerm = document.getElementById('searchName').value.toLowerCase();
        if (searchTerm.trim() === '') renderStudentTable(students);
        else renderStudentTable(students.filter(student => student.name.toLowerCase().includes(searchTerm) || (student.matricula && student.matricula.toLowerCase().includes(searchTerm)))); // Search by matricula too
    }
    function exportData() {
         const data = { students: students, users: users };
         const dataStr = JSON.stringify(data, null, 2); // Pretty print JSON
         const blob = new Blob([dataStr], { type: 'application/json' });
         const url = URL.createObjectURL(blob);
         const a = document.createElement('a');
         a.href = url;
         a.download = 'escola_academia_primeiros_passos_boletim_backup_' + new Date().toISOString().slice(0,10) + '.json'; // Filename with date
         document.body.appendChild(a); // Required for Firefox
         a.click();
         document.body.removeChild(a);
         URL.revokeObjectURL(url); // Clean up
         alert('Dados exportados com sucesso!');
    }

    function importData() {
         const fileInput = document.getElementById('importFile');
         const file = fileInput.files[0];
         const importStatus = document.getElementById('importStatus');
         const performImportButton = document.getElementById('performImportButton');

         importStatus.textContent = ''; // Clear previous status

         if (!file) {
             importStatus.textContent = 'Por favor, selecione um arquivo para importar.';
             return;
         }

         const reader = new FileReader();
         reader.onload = function(event) {
             try {
                 const importedData = JSON.parse(event.target.result);
                 if (importedData.students && importedData.users) {
                     // Basic validation: check if arrays exist
                     if (Array.isArray(importedData.students) && Array.isArray(importedData.users)) {
                          // More detailed validation could be added here (e.g., check for required fields in objects)

                          // Check if the imported data contains an admin user
                          const importedAdmin = importedData.users.find(user => user.username === 'administrador' && user.role === 'admin');

                          if (!importedAdmin) {
                             importStatus.textContent = 'Erro de importação: O arquivo não contém um usuário administrador válido.';
                             performImportButton.disabled = true; // Disable import again on error
                             document.getElementById('importFileName').textContent = 'Nenhum arquivo selecionado.';
                             fileInput.value = ''; // Clear file input
                             return;
                          }

                          // Keep the existing admin password for security (don't overwrite with imported password)
                          const existingAdmin = users.find(user => user.username === 'administrador' && user.role === 'admin');
                          if (existingAdmin) {
                              // Find the imported admin user and update its password to the existing one
                              const importedAdminUser = importedData.users.find(user => user.username === 'administrador' && user.role === 'admin');
                              if(importedAdminUser) {
                                 importedAdminUser.password = existingAdmin.password;
                                 // Also ensure its assignments are an array if missing
                                 if (!Array.isArray(importedAdminUser.assignments)) importedAdminUser.assignments = [];
                              }
                          } else {
                              // If somehow the existing admin is missing, add the imported one but issue a warning
                              alert('Aviso: O usuário administrador existente foi substituído pelo do arquivo importado. A senha padrão será usada.');
                               if (!Array.isArray(importedData.users[0].assignments)) importedData.users[0].assignments = []; // Ensure assignments is array for imported admin
                          }


                          students = importedData.students;
                          users = importedData.users;

                          // Ensure all imported users have an assignments array if they are professors or if the field is missing
                           students = students.map(s => { // NEW: Ensure professorNotes and matricula for students
                               if (!Array.isArray(s.professorNotes)) s.professorNotes = [];
                               if (!s.matricula) s.matricula = ''; // Ensure matricula for existing students
                               return s;
                           });

                           users = users.map(user => {
                               if (user.role === 'professor' && !Array.isArray(user.assignments)) {
                                   user.assignments = []; // Default to empty array if missing for professor
                               } else if (!Array.isArray(user.assignments)) {
                                   user.assignments = []; // Ensure assignments is an array for all users
                               }
                               return user;
                           });

                          saveData(); // Save the imported data
                          importStatus.textContent = 'Dados importados com sucesso!';
                          // Refresh UI based on the current user and imported data
                          if (currentUser) {
                               const updatedCurrentUser = users.find(user => user.username === currentUser.username && user.role === currentUser.role);
                               if (updatedCurrentUser) {
                                   currentUser = updatedCurrentUser; // Update currentUser reference
                                    if (currentUser.role === 'aluno') {
                                         // Try to relink student to the new username (matricula)
                                        const student = students.find(s => s.matricula && s.matricula.trim().toLowerCase() === currentUser.username.trim().toLowerCase());
                                         if (student) {
                                            currentUser.studentId = student.id;
                                         } else {
                                             console.warn('Could not relink student data after import for user:', currentUser.username);
                                              // Decide how to handle this - maybe show a specific message or log out
                                         }
                                         showStudentBulletin(); // Refresh bulletin for the student
                                    } else if (currentUser.role === 'admin' || currentUser.role === 'coordenador') {
                                         showStudentManagementSection(); // Refresh student management for admin/coordinator
                                    } else if (currentUser.role === 'professor') {
                                         showProfessorSection(currentUser); // Refresh professor section for professor
                                    }
                               } else {
                                    // Current user no longer exists in imported data, force logout
                                    alert('Seu usuário não foi encontrado nos dados importados. Você será desconectado.');
                                    logout();
                               }
                          } else {
                                // If no user was logged in, just render the tables with new data
                                 renderStudentTable(students);
                                 renderUsersTable(users);
                          }

                     } else {
                          importStatus.textContent = 'Erro de importação: Formato de dados inválido.';
                           performImportButton.disabled = true; // Disable import again on error
                           document.getElementById('importFileName').textContent = 'Nenhum arquivo selecionado.';
                           fileInput.value = ''; // Clear file input
                     }
                 } else {
                     importStatus.textContent = 'Erro de importação: O arquivo JSON não contém as chaves "students" e "users".';
                      performImportButton.disabled = true; // Disable import again on error
                      document.getElementById('importFileName').textContent = 'Nenhum arquivo selecionado.';
                      fileInput.value = ''; // Clear file input
                 }
             } catch (e) {
                 importStatus.textContent = 'Erro ao processar arquivo JSON: ' + e.message;
                  performImportButton.disabled = true; // Disable import again on error
                  document.getElementById('importFileName').textContent = 'Nenhum arquivo selecionado.';
                  fileInput.value = ''; // Clear file input
             } finally {
                 // Clear the file input regardless of success or failure for security/cleanup
                 fileInput.value = '';
             }
         };
         reader.readAsText(file); // Read the file as text
         performImportButton.disabled = true; // Disable button after starting import
    }

    function deleteStudentDiscipline(event) {
        const button = event.target; const studentId = button.dataset.studentId; const disciplineName = button.dataset.disciplineName; const unitNumber = parseInt(button.dataset.unitNumber);
        const student = students.find(s => s.id === studentId); if (!student) { alert('Erro: Aluno não encontrado para exclusão da disciplina.'); return; }
        const disciplineIndex = student.disciplines.findIndex(d => d.discipline === disciplineName && d.unit === unitNumber);
        if (disciplineIndex === -1) { alert('Erro: Entrada de disciplina não encontrada para exclusão.'); return; }
        if (confirm(`Tem certeza que deseja excluir a disciplina "${disciplineName}" (Unidade ${unitNumber}) para o aluno "${student.name}"? Esta ação não pode ser desfeita."`)) {
            student.disciplines.splice(disciplineIndex, 1);
            saveData(); // Save data after deleting a discipline
            renderStudentTable(students);
            if (currentUser && currentUser.role === 'professor') loadProfessorTable();
            if (currentUser && currentUser.role === 'aluno' && currentUser.studentId === student.id) showStudentBulletin();
            alert('Disciplina excluída com sucesso.');
        }
    }
    function attachDeleteButtonListeners(tableSelector) {
        const table = document.querySelector(tableSelector); if (!table) return;
        const tableBody = table.querySelector('tbody');
        if (tableBody) { tableBody.removeEventListener('click', handleTableButtonClick); tableBody.addEventListener('click', handleTableButtonClick); }
    }
    function handleTableButtonClick(event) { if (event.target.classList.contains('delete-button')) deleteStudentDiscipline(event); }
    document.getElementById('importFile').addEventListener('change', function(event) {
        const fileNameSpan = document.getElementById('importFileName'); const performImportButton = document.getElementById('performImportButton'); const file = event.target.files[0];
        if (file) { fileNameSpan.textContent = file.name; performImportButton.disabled = false; } else { fileNameSpan.textContent = 'Nenhum arquivo selecionado.'; performImportButton.disabled = true; }
        document.getElementById('importStatus').textContent = '';
    });

    const allClasses = [
        "ED. Infantil 1 Turma A", "ED. Infantil 1 Turma B", "ED. Infantil 1 Turma C", "ED. Infantil 1 Turma D",
        "ED. Infantil 2 Turma A", "ED. Infantil 2 Turma B", "ED. Infantil 2 Turma C", "ED. Infantil 2 Turma D",
        "ED. Infantil 3 Turma A", "ED. Infantil 3 Turma B", "ED. Infantil 3 Turma C", "ED. Infantil 3 Turma D",
        "1 ANO A Fundamental 1", "1 ANO B Fundamental 1", "1 ANO C Fundamental 1", "1 ANO D Fundamental 1",
        "2 ANO A Fundamental 1", "2 ANO B Fundamental 1", "2 ANO C Fundamental 1", "2 ANO D Fundamental 1",
        "3 ANO A Fundamental 1", "3 ANO B Fundamental 1", "3 ANO C Fundamental 1", "3 ANO D Fundamental 1",
        "4 ANO A Fundamental 1", "4 ANO B Fundamental 1", "4 ANO C Fundamental 1", "4 ANO D Fundamental 1",
        "5 ANO A Fundamental 1", "5 ANO B Fundamental 1", "5 ANO C Fundamental 1", "5 ANO D Fundamental 1",
        "6 ANO A Fundamental 2", "6 ANO B Fundamental 2", "6 ANO C Fundamental 2", "6 ANO D Fundamental 2",
        "7 ANO A Fundamental 2", "7 ANO B Fundamental 2", "7 ANO C Fundamental 2", "7 ANO D Fundamental 2",
        "8 ANO A Fundamental 2", "8 ANO B Fundamental 2", "8 ANO C Fundamental 2", "8 ANO D Fundamental 2",
        "9 ANO A Fundamental 2", "9 ANO B Fundamental 2", "9 ANO C Fundamental 2", "9 ANO D Fundamental 2",
        "1 ANO A Ensino Médio", "1 ANO B Ensino Médio", "1 ANO C Ensino Médio", "1 ANO D Ensino Médio",
        "2 ANO A Ensino Médio", "2 ANO B Ensino Médio", "2 ANO C Ensino Médio", "2 ANO D Ensino Médio",
        "3 ANO A Ensino Médio", "3 ANO B Ensino Médio", "3 ANO C Ensino Médio", "3 ANO D Ensino Médio"
    ].sort(); // Sort alphabetically for display

     const allDisciplines = [
        "Alfabetização", "Português", "Matemática", "Ciências", "História", "Geografia", "Artes", "Educação Física", "Inglês",
        "Redação", "Gramática", "Literatura", "Filosofia", "Física", "Química", "Biologia", "Sociologia", "ED. Ambiental"
     ].sort(); // Sort alphabetically for display


     // New function to populate the discipline and class checkboxes for professor assignment
    function populateProfessorAssignmentCheckboxes(containerElement, assignedAssignments = []) {
        containerElement.innerHTML = ''; // Clear previous content

        allDisciplines.forEach(discipline => {
            const disciplineDiv = document.createElement('div');
            disciplineDiv.classList.add('discipline-assignment');
            disciplineDiv.dataset.discipline = discipline; // Store discipline name for easy access

            const disciplineTitle = document.createElement('h4');
            disciplineTitle.textContent = discipline;
            disciplineDiv.appendChild(disciplineTitle);

            const classesDiv = document.createElement('div');
            classesDiv.classList.add('class-checkboxes');

            allClasses.forEach(className => {
                const label = document.createElement('label');
                const checkbox = document.createElement('input');
                checkbox.type = 'checkbox';
                checkbox.value = className;
                // Check if this discipline in this class is already assigned
                const isAssigned = assignedAssignments.some(assignment =>
                    assignment.discipline === discipline && assignment.classes.includes(className)
                );
                if (isAssigned) {
                    checkbox.checked = true;
                }

                label.appendChild(checkbox);
                label.appendChild(document.createTextNode(className));
                classesDiv.appendChild(label);
            });

            disciplineDiv.appendChild(classesDiv);
            containerElement.appendChild(disciplineDiv);
        });
    }


    document.getElementById('disciplineClassSelect').addEventListener('change', function() { populateStudentSelectForDiscipline(this.value); });
    document.getElementById('printClassSelect').addEventListener('change', function() { populateStudentPrintSelect(this.value); });
    function showAddAlunoUserForm() { const turmaSelect = document.getElementById('newAlunoTurmaSelect'); populateClassSelect(turmaSelect); document.getElementById('newAlunoNameInput').value = ''; document.getElementById('newAlunoMatriculaInput').value = ''; document.getElementById('newAlunoSenhaInput').value = ''; document.getElementById('newAlunoTurmaSelect').value = ''; document.getElementById('addAlunoUserModal').classList.remove('hidden'); }
    function saveAlunoUser() {
        const name = document.getElementById('newAlunoNameInput').value.trim(); const matricula = document.getElementById('newAlunoMatriculaInput').value.trim(); const senha = document.getElementById('newAlunoSenhaInput').value; const turma = document.getElementById('newAlunoTurmaSelect').value;
        if (!name || !matricula || !senha || !turma) { alert('Por favor, preencha Nome, Matrícula, Senha e selecione a Turma para o aluno.'); return; }
        if (users.some(user => user.username === matricula)) { alert(`Nome de usuário (matrícula) "${matricula}" já existe. Por favor, use uma matrícula única.`); return; }
        const correspondingStudents = students.filter(student => student.name.trim().toLowerCase() === name.trim().toLowerCase() && student.class === turma);
        let studentIdToLink = null;
        if (correspondingStudents.length === 0) { alert(`Erro: Nenhum aluno encontrado com o nome "${name}" na turma "${turma}". O usuário não foi criado.`); return; }
        else if (correspondingStudents.length > 1) { alert(`Erro: Múltiplos alunos encontrados com o nome "${name}" na turma "${turma}". Não é possível criar o usuário.`); return; }
        else { studentIdToLink = correspondingStudents[0].id; }
        users.push({ username: matricula, password: senha, role: 'aluno', name: name, studentId: studentIdToLink, assignments: [] }); // Aluno users have empty assignments
        saveData(); // Save data after adding an aluno user
        closeAddAlunoUserModal(); renderUsersTable(users); alert('Usuário de aluno adicionado com sucesso!');
    }
    function closeAddAlunoUserModal() { document.getElementById('addAlunoUserModal').classList.add('hidden'); document.getElementById('newAlunoNameInput').value = ''; document.getElementById('newAlunoMatriculaInput').value = ''; document.getElementById('newAlunoSenhaInput').value = ''; document.getElementById('newAlunoTurmaSelect').value = ''; }

    // MODIFICADA: printMyBulletin para usar seleções do aluno
    function printMyBulletin() {
        if (!currentUser || currentUser.role !== 'aluno') {
            alert('Esta função está disponível apenas para usuários aluno logados.');
            return;
        }
        const student = students.find(s => s.id === currentUser.studentId);
        if (!student) {
            alert('Não foi possível encontrar seus dados de boletim para impressão.');
            return;
        }

        // Pegar unidades selecionadas pelo aluno
        const selectedUnits = Array.from(document.querySelectorAll('#studentPrintOptions .studentUnitCheckboxPrint:checked')).map(cb => parseInt(cb.value));
        // Pegar tipo de relatório selecionado pelo aluno
        const reportType = document.querySelector('#studentPrintOptions input[name="studentReportType"]:checked').value;

        if (selectedUnits.length === 0) {
            alert('Por favor, selecione pelo menos uma unidade para imprimir.');
            return;
        }

        const bulletinHTML = generateBulletinHTML(student, selectedUnits, reportType, true); // Pass true to include notes
        openPrintWindow(bulletinHTML, `Boletim de ${student.name}`);
    }

    // NEW: Functions for Professor Notes Section

    function populateProfessorNotesControls() {
        const notesDisciplineSelect = document.getElementById('notesDisciplineSelect');
        const notesClassSelect = document.getElementById('notesClassSelect');
        const notesStudentSelect = document.getElementById('notesStudentSelect');
        const notesUnitSelect = document.getElementById('notesUnitSelect');

        notesDisciplineSelect.innerHTML = '<option value="">Selecione a Disciplina</option>';
        notesClassSelect.innerHTML = '<option value="">Selecione a Turma</option>';
        notesStudentSelect.innerHTML = '<option value="">Selecione o Aluno</option>';
        notesClassSelect.disabled = true;
        notesStudentSelect.disabled = true;

        if (currentUser && currentUser.assignments) {
            const uniqueDisciplines = [...new Set(currentUser.assignments.map(a => a.discipline))].sort();
            uniqueDisciplines.forEach(discipline => {
                const option = document.createElement('option');
                option.value = discipline;
                option.textContent = discipline;
                notesDisciplineSelect.appendChild(option);
            });
        }

        notesDisciplineSelect.removeEventListener('change', updateNotesClassSelect);
        notesDisciplineSelect.addEventListener('change', updateNotesClassSelect);

        notesClassSelect.removeEventListener('change', updateNotesStudentSelect);
        notesClassSelect.addEventListener('change', updateNotesStudentSelect);

        notesStudentSelect.removeEventListener('change', loadProfessorStudentNotes);
        notesStudentSelect.addEventListener('change', loadProfessorStudentNotes);

        notesUnitSelect.removeEventListener('change', loadProfessorStudentNotes);
        notesUnitSelect.addEventListener('change', loadProfessorStudentNotes);
    }

    function updateNotesClassSelect() {
        const notesDisciplineSelect = document.getElementById('notesDisciplineSelect');
        const notesClassSelect = document.getElementById('notesClassSelect');
        const selectedDiscipline = notesDisciplineSelect.value;

        notesClassSelect.innerHTML = '<option value="">Selecione a Turma</option>';
        notesClassSelect.disabled = true;
        document.getElementById('notesStudentSelect').innerHTML = '<option value="">Selecione o Aluno</option>';
        document.getElementById('notesStudentSelect').disabled = true;
        document.getElementById('professorNoteContent').value = '';
        document.getElementById('existingProfessorNotes').innerHTML = '<p class="no-notes" style="text-align: center; font-style: italic;">Selecione aluno, disciplina e unidade para ver ou adicionar anotações.</p>';

        if (currentUser && currentUser.assignments && selectedDiscipline) {
            const assignment = currentUser.assignments.find(a => a.discipline === selectedDiscipline);
            if (assignment && assignment.classes.length > 0) {
                assignment.classes.sort().forEach(className => {
                    const option = document.createElement('option');
                    option.value = className;
                    option.textContent = className;
                    notesClassSelect.appendChild(option);
                });
                notesClassSelect.disabled = false;
            }
        }
    }

    function updateNotesStudentSelect() {
        const notesClassSelect = document.getElementById('notesClassSelect');
        const notesStudentSelect = document.getElementById('notesStudentSelect');
        const selectedClass = notesClassSelect.value;

        notesStudentSelect.innerHTML = '<option value="">Selecione o Aluno</option>';
        notesStudentSelect.disabled = true;
        document.getElementById('professorNoteContent').value = '';
        document.getElementById('existingProfessorNotes').innerHTML = '<p class="no-notes" style="text-align: center; font-style: italic;">Selecione aluno, disciplina e unidade para ver ou adicionar anotações.</p>';

        if (selectedClass) {
            const studentsInClass = students.filter(s => s.class === selectedClass);
            if (studentsInClass.length > 0) {
                studentsInClass.sort((a, b) => a.name.localeCompare(b.name)).forEach(student => {
                    const option = document.createElement('option');
                    option.value = student.id;
                    option.textContent = `${student.name} (${student.matricula})`; // Display matricula in notes student select
                    notesStudentSelect.appendChild(option);
                });
                notesStudentSelect.disabled = false;
            }
        }
    }

    function loadProfessorStudentNotes() {
        const notesStudentSelect = document.getElementById('notesStudentSelect');
        const notesDisciplineSelect = document.getElementById('notesDisciplineSelect');
        const notesUnitSelect = document.getElementById('notesUnitSelect');
        const existingNotesDiv = document.getElementById('existingProfessorNotes');

        const studentId = notesStudentSelect.value;
        const discipline = notesDisciplineSelect.value;
        const unit = parseInt(notesUnitSelect.value);

        existingNotesDiv.innerHTML = '';
        if (!studentId || !discipline || !unit) {
            existingNotesDiv.innerHTML = '<p class="no-notes" style="text-align: center; font-style: italic;">Selecione aluno, disciplina e unidade para ver ou adicionar anotações.</p>';
            return;
        }

        const student = students.find(s => s.id === studentId);
        if (student && student.professorNotes) {
            const relevantNotes = student.professorNotes.filter(note =>
                note.discipline === discipline && note.unit === unit
            ).sort((a, b) => new Date(b.date) - new Date(a.date)); // Sort by date descending

            if (relevantNotes.length > 0) {
                relevantNotes.forEach((note, index) => {
                    const noteItem = document.createElement('div');
                    noteItem.classList.add('professor-note-item');
                    noteItem.innerHTML = `
                        <p><strong>Anotação:</strong> ${note.content}</p>
                        <span class="note-meta">Feita por: ${note.professorName} em ${new Date(note.date).toLocaleDateString()}</span>
                        <button class="delete-note-button" data-student-id="${student.id}" data-note-index="${index}">Excluir</button>
                    `;
                    existingNotesDiv.appendChild(noteItem);
                });
                attachDeleteNoteButtonListeners(); // Attach listeners for newly rendered buttons
            } else {
                existingNotesDiv.innerHTML = '<p class="no-notes" style="text-align: center; font-style: italic;">Nenhuma anotação existente para esta seleção.</p>';
            }
        } else {
            existingNotesDiv.innerHTML = '<p class="no-notes" style="text-align: center; font-style: italic;">Nenhuma anotação existente para esta seleção.</p>';
        }
    }

    function saveProfessorNote() {
        const notesStudentSelect = document.getElementById('notesStudentSelect');
        const notesDisciplineSelect = document.getElementById('notesDisciplineSelect');
        const notesUnitSelect = document.getElementById('notesUnitSelect');
        const professorNoteContent = document.getElementById('professorNoteContent');

        const studentId = notesStudentSelect.value;
        const discipline = notesDisciplineSelect.value;
        const unit = parseInt(notesUnitSelect.value);
        const content = professorNoteContent.value.trim();

        if (!studentId || !discipline || !unit || !content) {
            alert('Por favor, selecione o Aluno, Disciplina, Unidade e escreva o conteúdo da anotação.');
            return;
        }

        const student = students.find(s => s.id === studentId);
        if (student) {
            const newNote = {
                professorName: currentUser.name,
                discipline: discipline,
                unit: unit,
                date: new Date().toISOString(), // ISO string for easy storage and parsing
                content: content
            };
            student.professorNotes.push(newNote);
            saveData();
            professorNoteContent.value = ''; // Clear textarea
            loadProfessorStudentNotes(); // Reload notes display
            if (currentUser.role === 'aluno' && currentUser.studentId === student.id) showStudentBulletin(); // Update student view if it's their bulletin
            alert('Anotação salva com sucesso!');
        } else {
            alert('Aluno não encontrado para salvar anotação.');
        }
    }

    function deleteProfessorNote(studentId, noteIndex) {
        const student = students.find(s => s.id === studentId);
        if (student && student.professorNotes && student.professorNotes.length > noteIndex) {
            if (confirm('Tem certeza que deseja excluir esta anotação?')) {
                student.professorNotes.splice(noteIndex, 1);
                saveData();
                loadProfessorStudentNotes(); // Reload notes display
                if (currentUser.role === 'aluno' && currentUser.studentId === student.id) showStudentBulletin(); // Update student view if it's their bulletin
                alert('Anotação excluída.');
            }
        } else {
            alert('Erro: Anotação não encontrada.');
        }
    }

    function attachDeleteNoteButtonListeners() {
        document.querySelectorAll('.professor-note-item .delete-note-button').forEach(button => {
            button.removeEventListener('click', handleDeleteNoteClick); // Prevent multiple listeners
            button.addEventListener('click', handleDeleteNoteClick);
        });
    }

    function handleDeleteNoteClick(event) {
        const studentId = event.target.dataset.studentId;
        const noteIndex = parseInt(event.target.dataset.noteIndex);
        deleteProfessorNote(studentId, noteIndex);
    }

    // NEW: Function to display notes for the student in their bulletin
    function displayStudentNotes(student) {
        const studentNotesContent = document.getElementById('studentNotesContent');
        studentNotesContent.innerHTML = ''; // Clear existing content

        if (!student || !student.professorNotes || student.professorNotes.length === 0) {
            studentNotesContent.innerHTML = '<p class="no-notes">Nenhuma anotação disponível.</p>';
            return;
        }

        // Sort notes by date (descending), then discipline, then professor
        const sortedNotes = student.professorNotes.slice().sort((a, b) => {
            const dateA = new Date(a.date);
            const dateB = new Date(b.date);
            if (dateA.getTime() !== dateB.getTime()) return dateB.getTime() - dateA.getTime();
            if (a.discipline !== b.discipline) return a.discipline.localeCompare(b.discipline);
            return a.professorName.localeCompare(b.professorName);
        });

        sortedNotes.forEach(note => {
            const noteItem = document.createElement('div');
            noteItem.classList.add('professor-note-item');
            noteItem.innerHTML = `
                <p><strong>Disciplina:</strong> ${note.discipline}, <strong>Unidade:</strong> ${note.unit}</p>
                <p><strong>Anotação:</strong> ${note.content}</p>
                <span class="note-meta">Feita por: ${note.professorName} em ${new Date(note.date).toLocaleDateString()}</span>
            `;
            studentNotesContent.appendChild(noteItem);
        });
    }

</script>

<div class="modal hidden" id="addAlunoUserModal">
<div class="modal-content">
<span class="close-button" onclick="closeAddAlunoUserModal()">×</span>
<h2>Adicionar Usuário de Aluno</h2>
<div>
<label for="newAlunoNameInput">Nome do Aluno:</label>
<input id="newAlunoNameInput" placeholder="Nome completo do aluno" type="text"/>
</div>
<div>
<label for="newAlunoMatriculaInput">Matrícula:</label>
<input id="newAlunoMatriculaInput" placeholder="Matrícula do aluno" type="text"/>
</div>
<div>
<label for="newAlunoSenhaInput">Senha:</label>
<input id="newAlunoSenhaInput" placeholder="Senha para login do aluno" type="password"/>
</div>
<div>
<label for="newAlunoTurmaSelect">Turma:</label>
<select id="newAlunoTurmaSelect">
<option value="">Selecione a Turma</option>
</select>
</div>
<button class="button" onclick="saveAlunoUser()" type="button">Salvar Aluno</button>
</div>
</div>
</body>
</html>
