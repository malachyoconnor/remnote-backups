- Snippet
    - ```css
 -
- # tskn's Theme
    - Light, modern theme. Design by tskn, code by Eva Thomas. See the Homepage for proper attribution.
    - id: com.github.hannesfrank.remnote-library.tskn-theme
    - version: 1.1.0
    - [Homepage](https://github.com/ethomasv/RemNoteTheme)
    - [Report Problem or Suggest Improvement](https://github.com/ethomasv/RemNoteTheme/issues/new?title=RemNote%20Library%20Report%3A%20tskn%27s%20Theme%20v1.1.0&body=%0A%2A%2APlease%20check%20first%20if%20there%20is%20an%20update%20of%20this%20scroll%20available.%2A%2A%0A%0A---%0A%0A-%20%2A%2AId%3A%2A%2A%20com.github.hannesfrank.remnote-library.tskn-theme%0A-%20%2A%2AVersion%3A%2A%2A%201.1.0%0A-%20%2A%2AType%3A%2A%2A%20Problem/Suggestion%20%28choose%20one%29%0A%0A-%20%5B%20%5D%20Describe%20the%20problem%20you%20are%20having%20with%20the%20scroll%20or%20how%20it%20should%20be%20improved.%0A-%20%5B%20%5D%20_Add_%20a%20short%20description%20to%20the%20title%20%28don%27t%20replace%20it%20completely%21%29%20so%20people%20know%20what%20this%20is%20about.%0A-%20%5B%20%5D%20Make%20sure%20to%20include%20a%20screenshot%20or%20image%20to%20make%20your%20issue%20easy%20to%20understand.%0A%0A---%0A)
    - ## Code
        - [ ] Hide Indented Rem Indicator |
            ```css
            .rem-indented-indicator {
              display: none;
            }
            ```
        - [x] Hide Cloze Menu Button while editing
            ```css
            i.icon.caret.square.down.icon:before {
              display: none;
            }

            i.icon.caret.square.down.icon:after {
              content: "+";
            }
            ```
        - [x] Show Reference Brackets [ ]
            ```css
            .rem-reference-link:before {
              content: "[";
            }

            .rem-reference-link:after {
              content: "]";
            }
            ```
        - [x] Custom Scroll Bar
            ```css
            div::-webkit-scrollbar {
              width: 0px !important;
              height: 2px !important;
            }

            div::-webkit-scrollbar-track {
              background-color: transparent !important;
            }

            div::-webkit-scrollbar-thumb {
              background-color: rgba(255, 255, 255, 0.4) !important;
              border-radius: 10px !important;
            }

            div::-webkit-scrollbar-thumb:hover {
              background-color: rgba(255, 255, 255, 0.4) !important;
            }
            ```
        - **Choose one:** Spacing and Header Size
            - [x] Roomy Spacing and Large Headers
                ```css
                :root {
                  --spacing-line-height: 1.5em;
                  --spacing-tree-node-container-margin-top: 0.5em;
                  --spacing-bullet-paragraph-margin-top: 7px;
                  --spacing-bullet-document-margin-top: 3px;
                  --spacing-bullet-conceptDescriptor-margin-top: 7px;

                  --header-1-margin-top: 20px;
                  --header-2-margin-top: 11px;
                  --header-3-margin-top: 6px;

                  --header-1-font-size: 25px;
                  --header-1-font-weight: 500;
                  --header-2-font-size: 19px;
                  --header-2-font-weight: 600;
                  --header-3-font-size: 16px;
                  --header-3-font-weight: 700;
                }
                ```
            - [x] Roomy Spacing and Small Headers
                ```css
                :root {
                  --spacing-line-height: 1.5em;
                  --spacing-tree-node-container-margin-top: 0.5em;
                  --spacing-bullet-paragraph-margin-top: 7px;
                  --spacing-bullet-document-margin-top: 3px;
                  --spacing-bullet-conceptDescriptor-margin-top: 7px;

                  --header-1-margin-top: 11px;
                  --header-2-margin-top: 8px;
                  --header-3-margin-top: 6px;

                  --header-1-font-size: 18px;
                  --header-1-font-weight: 500;
                  --header-2-font-size: 16px;
                  --header-2-font-weight: 600;
                  --header-3-font-size: 15px;
                  --header-3-font-weight: 500;
                }
                ```
            - [x] Compact Spacing and Large Headers
                ```css
                :root {
                  --spacing-line-height: 1.3em;
                  --spacing-tree-node-container-margin-top: 0em;
                  --spacing-bullet-paragraph-margin-top: 4px;
                  --spacing-bullet-document-margin-top: 3px;
                  --spacing-bullet-conceptDescriptor-margin-top: 4px;

                  --header-1-margin-top: 18px;
                  --header-2-margin-top: 8px;
                  --header-3-margin-top: 3px;

                  --header-1-font-size: 25px;
                  --header-1-font-weight: 500;
                  --header-2-font-size: 19px;
                  --header-2-font-weight: 600;
                  --header-3-font-size: 16px;
                  --header-3-font-weight: 700;
                }
                ```
            - [x] Compact Spacing and Small Headers
                ```css
                :root {
                  --spacing-line-height: 1.3em;
                  --spacing-tree-node-container-margin-top: 0em;
                  --spacing-bullet-paragraph-margin-top: 4px;
                  --spacing-bullet-document-margin-top: 3px;
                  --spacing-bullet-conceptDescriptor-margin-top: 4px;
  
                  --header-1-margin-top: 8px;
                  --header-2-margin-top: 5px;
                  --header-3-margin-top: 3px;

                  --header-1-font-size: 18px;
                  --header-1-font-weight: 500;
                  --header-2-font-size: 16px;
                  --header-2-font-weight: 600;
                  --header-3-font-size: 15px;
                  --header-3-font-weight: 500;
                }
                ```
        - Theme
            ```css
            /*
            @version        1.1.0
            @description    RemNote Theme Designed by tskn > https://dribbble.com/shots/14178356-RemNote-Concept
            @author         Code by Eva Thomas 
            @homepageURL    https://github.com/ethomasv/RemNoteTheme
            */

            /* === Changes from the original theme. === */

            /* Code nodes should always be monospace. The theme otherwise sets the font of every div */
            #code-node {
              font-family: monaco, menlo, consolas, courier new;
            }

            /* === Original theme below (see also factored out modules) === */
            div {
              line-height: var(--spacing-line-height, 1.5em);
            }

            .tree-node-container {
              margin-top: var(--spacing-tree-node-container-margin-top, 0.5em);
            }

            /* Paragraph Bullet */
            .rem-bullet__container .rem-bullet.rem-bullet--all-children-visible {
              margin-top: var(--spacing-bullet-paragraph-margin-top, 7px);
            }

            .rem-bullet__container .rem-bullet.rem-bullet--hidden-children {
              margin-top: var(--spacing-bullet-paragraph-margin-top, 7px);
            }

            /* Document Bullet */
            .file.small.icon.rem-bullet__icon.rem-bullet--hidden-children,
            .file.small.icon.rem-bullet__icon.rem-bullet--all-children-visible {
              margin-top: var(--spacing-bullet-document-margin-top, 3px);
            }

            .file.small.icon.rem-bullet__icon.rem-bullet--hidden-children {
              margin-top: var(--spacing-bullet-document-margin-top, 3px);
            }

            /* Folder Bullet */
            .folder.small.icon.rem-bullet__icon.rem-bullet--hidden-children,
            .folder.small.icon.rem-bullet__icon.rem-bullet--all-children-visible {
              margin-top: var(--spacing-bullet-document-margin-top, 3px);
            }

            .folder.small.icon.rem-bullet__icon.rem-bullet--hidden-children {
              margin-top: var(--spacing-bullet-document-margin-top, 3px);
            }

            /* Concept Rem type Bullet */
            .rem-container--concept-rem-type
              .rem-bullet__container
              .rem-bullet.rem-bullet--all-children-visible {
              margin-top: var(--spacing-bullet-conceptDescriptor-margin-top, 7px);
            }

            .rem-container--concept-rem-type
              .rem-bullet__container
              .rem-bullet.rem-bullet--hidden-children {
              margin-top: var(--spacing-bullet-conceptDescriptor-margin-top, 7px);
            }

            /* Descriptor Rem type Bullet */
            .rem-container--descriptor-rem-type
              .rem-bullet__container
              .rem-bullet.rem-bullet--all-children-visible {
              margin-top: var(--spacing-bullet-conceptDescriptor-margin-top, 7px);
            }

            .rem-container--descriptor-rem-type
              .rem-bullet__container
              .rem-bullet.rem-bullet--hidden-children {
              margin-top: var(--spacing-bullet-conceptDescriptor-margin-top, 7px);
            }

            /* Header */
            .rem-bullet__container .rem-bullet.rem-header__bullet--1 {
              margin-top: var(--header-1-margin-top, 11px);
            }

            .rem-bullet__container .rem-bullet.rem-header__bullet--2 {
              margin-top: var(--header-2-margin-top, 8px);
            }

            .rem-bullet__container .rem-bullet.rem-header__bullet--3 {
              margin-top: var(--header-3-margin-top, 6px);
            }

            .rem-text.rem-header--1 {
              font-size: var(--header-1-font-size, 18px);
              font-weight: var(--header-1-font-weight, 500);
            }

            .rem-text.rem-header--2 {
              font-size: var(--header-2-font-size, 16px);
              font-weight: var(--header-2-font-weight, 600);
            }

            .rem-text.rem-header--3 {
              font-size: var(--header-3-font-size, 15px);
              font-weight: var(--header-3-font-weight, 500);
            }

            /* Documents List */
            .ReactVirtualized__Table__headerRow {
              text-align: center;
              font-weight: 500;
              letter-spacing: 0.01em;
              font-size: 13px;
              padding-bottom: 5px;
              margin-top: 25px;
            }

            .ReactVirtualized__Table__row[style*="background-color: rgba(1\, 1\, 1\, 0.1);"],
            .ReactVirtualized__Table__row {
              color: var(--font-c) !important;
              background-color: transparent !important;
              border-top: 1px solid var(--border-c);
            }

            .ReactVirtualized__Grid__innerScrollContainer > * {
              margin-top: 0px;
              margin-left: 20px;
            }

            #DocumentTable .DocumentLink:hover {
              background-color: transparent;
              color: var(--font-c) !important;
            }

            #DocumentTable .DocumentLink {
              color: var(--font-background-c) !important;
            }

            #DocumentTable a:hover,
            #DocumentTable .blackLinks a:hover {
              letter-spacing: -0.01em;
            }

            .ReactVirtualized__Table__rowColumn[style*="flex: 0 1 690px;"]:hover {
              background-color: #5da1b44d !important;
            }

            #DocumentTable .Cell {
              margin-left: auto;
              margin-right: auto;
            }

            /* Sidebar */
            #document-sidebar__link__queue-indicator {
              background-color: var(--hover-blue-c);
              padding: 5px;
            }

            #homepage #content #document-sidebar,
            #main #content #document-sidebar {
              background-color: var(--main-blue-c);
              color: white;
              border-right: 20px solid var(--main-blue-c);
              border-bottom: 2px solid var(--main-blue-c);
              padding: 10px 3px 10px 10px;
            }

            #document-sidebar #documentList #documentListScrollPortal .document-list-items {
              max-width: 240px;
            }

            #document-sidebar__link.document-sidebar__linkQueue {
              color: #fffc !important;
              font-weight: 400 !important;
              letter-spacing: 0.05em;
              font-size: 1.1em;
            }

            #document-sidebar__document-buttons__document-link-container,
            #document-sidebar__document-buttons__document-link-container
              .document-sidebar__link__icon-container {
              color: white;
              font-weight: 400 !important;
              letter-spacing: 0.05em;
              font-size: 1.1em;
            }

            #document-sidebar__document-buttons
              #document-sidebar__document-buttons__document-link-container:hover {
              background-color: var(--hover-blue-c);
            }

            #homepage #content #document-sidebar a:hover,
            #homepage #content #document-sidebar a:visited,
            #main #content #document-sidebar a:hover,
            #main #content #document-sidebar a:visited {
              color: white !important;
              opacity: 1;
            }

            #DocumentationList .document-list-item--opened,
            #documentList .document-list-item--opened {
              background-color: var(--hover-blue-c) !important;
              font-weight: 400;
            }

            #DocumentationList .document-list-item,
            #documentList .document-list-item {
              padding: 7px 0px;
            }

            .document-sidebar__linkOpen,
            #document-sidebar__link:hover,
            #DocumentationList .document-list-item:hover,
            #documentList .document-list-item:hover {
              background-color: var(--hover-blue-c) !important;
            }

            #document-sidebar #logo {
              display: none;
            }

            #document-sidebar #document-sidebar__account-capsule {
              background-color: transparent;
              color: white;
            }

            #document-sidebar #document-sidebar__collapse-icon,
            #document-sidebar .document-sidebar__document-buttons__button img,
            #document-sidebar .document-sidebar__bottom-buttons__button img,
            #document-sidebar
              .document-list-item__folder-icon.document-list-item__folder-icon--closed
              img,
            #document-sidebar
              #DocumentationList
              .folder-float-buttons
              .folder-float-button
              img,
            #document-sidebar
              #DocumentationList
              .document-list-item
              .document-list-item__folder-icon--opened
              img,
            #document-sidebar
              #documentList
              .document-list-item
              .document-list-item__folder-icon--opened
              img {
              filter: grayscale(100%) invert(100%) contrast(300%);
              opacity: 1;
            }

            #document-sidebar
              #document-sidebar__link
              .document-sidebar__link__icon-container
              img,
            #document-sidebar #documentList .folder-float-buttons .folder-float-button img {
              filter: invert(65%) brightness(200%);
            }

            #document-sidebar
              #document-sidebar__document-buttons__document-link-container
              i.file.icon,
            #document-sidebar i.arrow.alternate.circle.up.icon,
            .thinking-trail-history__document-dot__preview i.file.text.small.icon,
            #document-sidebar i.caret.right.icon {
              color: white;
            }

            #document-sidebar #DocumentationList .documentListCheckbox,
            #document-sidebar #documentList .documentListCheckbox {
              color: white;
            }

            #document-sidebar #DocumentationList .document-list-header,
            #document-sidebar #documentList .document-list-header {
              color: white;
              text-transform: uppercase;
              font-weight: 400 !important;
            }

            #document-sidebar #DocumentationList .document-list-header b,
            #document-sidebar #documentList .document-list-header b {
              font-weight: 400 !important;
              letter-spacing: 0.05em;
            }

            #document-sidebar #DocumentationList .document-list-header i.dropdown.icon,
            #document-sidebar #documentList .document-list-header i.dropdown.icon,
            .folderDocumentList i.dropdown.icon {
              color: white;
            }

            #document-sidebar #DocumentationList .folder-float-buttons,
            #document-sidebar #documentList .folder-float-buttons {
              background-color: inherit;
              margin-top: 4px;
              margin-right: 5px;
            }

            #document-sidebar
              #DocumentationList
              .folder-float-buttons
              .folder-float-button
              i,
            #document-sidebar #documentList .folder-float-buttons .folder-float-button i {
              color: white;
            }

            #document-sidebar i.icons .corner.icon {
              text-shadow: -1px -1px 0 var(--main-blue-c), 1px -1px 0 var(--main-blue-c),
                -1px 1px 0 var(--main-blue-c), 1px 1px 0 var(--main-blue-c);
            }

            #status-indicator__title,
            #status-indicator,
            #status-indicator__title i {
              color: white;
            }

            #document-sidebar--collapsed {
              background-color: var(--main-blue-c);
              z-index: 3;
              border: 1px solid var(--main-blue-c);
            }

            #document-sidebar--collapsed i.ellipsis.horizontal.large.icon {
              color: transparent;
            }

            #status-indicator__title,
            #status-indicator,
            #status-indicator__title i {
              background-color: transparent !important;
            }

            #document-sidebar.document-sidebar--floating {
              z-index: 5 !important;
            }

            #multiple-windows__document #multiple-windows__close-pane {
              opacity: 0.5;
              margin-top: -10px;
              margin-right: -2px;
            }

            #DocumentationList .documentListNoDocuments,
            #documentList .documentListNoDocuments {
              color: white;
              opacity: 0.9;
            }

            /* Thinking trail */
            #thinking-trail-history {
              margin-left: -20px;
              z-index: 4;
              background-color: var(--main-blue-c);
              width: 40px;
            }

            .small-window-page #thinking-trail-history {
              margin-left: 0px;
            }

            #thinking-trail-history__container {
              padding-bottom: 0px;
              padding-top: 25px !important;
              height: 100%;
              padding-left: 8.5px;
            }

            .multiple-windows--one-pane #thinking-trail-history {
              width: 20px;
            }

            .multiple-windows--two-panes #thinking-trail-history {
              width: 40px;
            }

            #thinking-trail-history
              #thinking-trail-history__document-list
              .thinking-trail-history__document-dot__preview:hover {
              background-color: var(--hover-blue-c);
              border: thin solid var(--soft-blue-c);
              border-radius: 4px;
              padding: 0px 6px !important;
            }

            #thinking-trail-history:hover #thinking-trail-history__container {
              background-color: var(--hover-blue-c);
              box-shadow: none;
              margin: 0px;
              border-right: 7px solid var(--hover-blue-c);
              height: 100vh;
              max-width: 500px;
            }

            #thinking-trail-history
              .thinking-trail-history__document
              .thinking-trail-history__document-dot {
              background-color: var(--soft-blue-c);
              border: 1px solid var(--soft-blue-c);
              border-radius: 5px;
              width: 5px;
              height: 5px;
              margin-left: -1px;
            }

            #thinking-trail-history
              .thinking-trail-history__document
              .thinking-trail-history__document-dot:hover,
            #thinking-trail-history .thinking-trail-history__document-dot--active {
              background-color: white !important;
              border: 1px solid white !important;
              border-radius: 5px !important;
              width: 7px !important;
              height: 7px !important;
              box-shadow: none !important;
              margin-left: -2px !important;
            }

            #thinking-trail-history
              .thinking-trail-history__document
              .thinking-trail-history__children-bar {
              color: var(--soft-blue-c);
            }

            #thinking-trail-history .thinking-trail-history__document-height-offset {
              padding-top: 0.9px;
            }

            #thinking-trail-history
              .thinking-trail-history__document
              .thinking-trail-history__document-height-offset {
              background-color: var(--soft-blue-c);
            }

            #thinking-trail-history
              .thinking-trail-history__document
              .thinking-trail-history__document-dot__preview {
              padding: 2px 7px 0px 5px;
            }

            #thinking-trail-history__document-list
              .thinking-trail-history__document-dot__preview:hover {
              color: white;
              padding: 1px 7px !important;
            }

            #thinking-trail-history
              #thinking-trail-history__document-list
              .thinking-trail-history__document-dot__preview {
              padding: 1px 7px;
              color: white;
              overflow: hidden;
              max-width: 370px;
              font-size: 12px;
            }

            #thinking-trail-history
              #thinking-trail-history__document-list
              .thinking-trail-history__document-dot__preview:hover {
              color: white;
            }

            #thinking-trail-history__container .grey.close.icon {
              color: white !important;
              padding-left: 7px;
            }

            /* Document Top Bar */
            .remHierarchyTop {
              width: 150vw !important;
              max-width: 150vw !important;
              min-width: 150vw !important;
              border-top: 1px solid var(--border-c);
              margin-left: -20vw;
              margin-top: 10px;
              height: 0px;
              visibility: visible !important;
              padding: 0px !important;
            }

            #homepage #content .DocumentationPageWrapper,
            #homepage #content .page,
            #main #content .DocumentationPageWrapper,
            #main #content .page {
              padding: 0px;
            }

            .document-source--hide-on-unfocus {
              opacity: 1 !important;
              visibility: visible;
            }

            #document-parents {
              padding-bottom: 15px;
              padding-top: 10px;
            }

            .document-source {
              padding-left: 0;
              padding-right: 0;
              padding-top: 20px;
              padding-bottom: 7px;
              visibility: visible;
            }

            #document #actionRequiredDocumentTitle,
            #document .document-title {
              font-size: 30px;
              font-weight: 500;
            }

            #document-parents .parent-link,
            #document-parents .join-arrow {
              opacity: 0.4;
            }

            #DocumentTitle .rem-header--1,
            #DocumentTitle .rem-header--2,
            #DocumentTitle .rem-header--3 {
              background-color: transparent;
              font-size: 30px;
              font-weight: 600;
            }

            /* Headers */
            .rem-text.rem-header--1,
            .rem-text.rem-header--2,
            .rem-text.rem-header--3 {
              border-radius: 7px;
              margin-left: -12px;
              padding-left: 29px !important;
            }

            .rem-text.rem-header--1,
            .rem-text.rem-header--2,
            .rem-text.rem-header--3 {
              background-color: rgb(244, 243, 239);
            }

            /* Highlighters */
            .highlight-color--orange {
              background-color: var(--highlight-orange-c, #ffc7c7) !important;
              padding: 0px 7px;
              border-radius: 4px;
            }

            .highlight-color--red {
              background-color: var(--highlight-red-c, #ffd599) !important;
              padding: 0px 7px;
              border-radius: 4px;
            }

            .highlight-color--blue {
              background-color: var(--highlight-blue-c, #fef49d) !important;
              padding: 0px 7px;
              border-radius: 4px;
            }

            .highlight-color--yellow {
              background-color: var(--highlight-yellow-c, #d7e985) !important;
              padding: 0px 7px;
              border-radius: 4px;
            }

            .highlight-color--green {
              background-color: var(--highlight-green-c, #e4b1eb) !important;
              padding: 0px 7px;
              border-radius: 4px;
            }

            .highlight-color--purple {
              background-color: var(--highlight-purple-c, #afd9fb) !important;
              padding: 0px 7px;
              border-radius: 4px;
            }

            /* Tags */
            .hierarchy-editor__tag-bar__tag.button i.arrow.alternate.circle.up.icon {
              padding-left: 4px;
              color: #999;
            }

            .hierarchy-editor__tag-bar__tag.button {
              padding: 3px 7px 4px 7px;
              font-size: 11px;
              opacity: 1;
              color: #999;
            }

            .hierarchy-editor__tag-bar__tag.button > span:before {
              content: " ";
            }

            .hierarchy-editor__tag-bar__tag.button > span {
              color: #555;
            }

            .hierarchy-editor__tag-bar__tag {
              background-color: #f4f3ef80;
            }

            .work-in-progress-tag {
              border-radius: 4px;
              color: var(--font-background-c);
              padding: 1px 5px;
              background-color: #f4f4f4;
            }

            /* Main */
            body {
              font-size: 13px;
              color: #222;
            }

            div {
              font-family: var(--font-body);
              font-size: 1em;
              margin: 0px;
              padding: 0px;
            }

            #code-node,
            #quote,
            .quote {
              background-color: var(--quote-background-c, #ecf3f6);
              border: none;
              border-radius: 3px;
              color: var(--font-c);
              padding-left: 7px;
              padding-right: 7px;
            }

            i.quote.right.icon {
              height: 16px;
              padding: 3px 7px;
            }

            :focus {
              outline: none;
            }

            .rem-text {
              padding-left: 20px !important;
            }

            #draggingIndicator,
            #draggingIndicatorAddAsChild {
              height: 2px;
              border: 2px solid var(--soft-blue-c);
              background-color: var(--soft-blue-c);
              border-radius: 10px !important;
              top: -2px;
            }

            /* Bullets */
            /* Main open and closed bullet for headers */
            .rem-bullet__container
              .rem-bullet.rem-bullet--all-children-visible.rem-header__bullet--1 {
              border: 2px solid var(--bullet-main);
              background-color: transparent;
              height: 7px !important;
              width: 7px !important;
            }

            .rem-bullet__container
              .rem-bullet.rem-bullet--hidden-children.rem-header__bullet--1 {
              border: 2px solid var(--bullet-main) !important;
              background-color: var(--bullet-main);
              height: 7px !important;
              width: 7px !important;
            }

            .rem-bullet__container
              .rem-bullet.rem-bullet--all-children-visible.rem-header__bullet--2 {
              border: 2px solid var(--bullet-main);
              background-color: transparent;
              height: 7px !important;
              width: 7px !important;
            }

            .rem-bullet__container
              .rem-bullet.rem-bullet--hidden-children.rem-header__bullet--2 {
              border: 2px solid var(--bullet-main) !important;
              background-color: var(--bullet-main);
              height: 7px !important;
              width: 7px !important;
            }

            .rem-bullet__container
              .rem-bullet.rem-bullet--all-children-visible.rem-header__bullet--3 {
              border: 2px solid var(--bullet-main);
              background-color: transparent;
              height: 7px !important;
              width: 7px !important;
            }

            .rem-bullet__container
              .rem-bullet.rem-bullet--hidden-children.rem-header__bullet--3 {
              border: 2px solid var(--bullet-main) !important;
              background-color: var(--bullet-main);
              height: 7px !important;
              width: 7px !important;
            }

            /* Paragraph Bullet */
            .rem-bullet__container .rem-bullet.rem-bullet--all-children-visible {
              border: 2px solid var(--bullet-main) !important;
              background-color: transparent;
              height: 7px !important;
              width: 7px !important;
            }

            .rem-bullet__container .rem-bullet.rem-bullet--hidden-children {
              border: 2px solid var(--bullet-main) !important;
              background-color: var(--bullet-main);
              height: 7px !important;
              width: 7px !important;
            }

            /* Document Bullet */
            .file.small.icon.rem-bullet__icon.rem-bullet--hidden-children,
            .file.small.icon.rem-bullet__icon.rem-bullet--all-children-visible {
              border: 2px solid var(--bullet-doc) !important;
              background-color: transparent;
              height: 7px !important;
              width: 7px !important;
              border-radius: 3px;
            }

            .file.small.icon.rem-bullet__icon.rem-bullet--hidden-children {
              border: 2px solid var(--bullet-doc) !important;
              background-color: var(--bullet-doc);
              height: 7px !important;
              width: 7px !important;
              border-radius: 3px;
            }

            .file.small.icon.rem-bullet__icon.rem-bullet--hidden-children::before,
            .file.small.icon.rem-bullet__icon.rem-bullet--all-children-visible::before {
              display: none;
            }

            /* Folder Bullet */
            .folder.small.icon.rem-bullet__icon.rem-bullet--hidden-children,
            .folder.small.icon.rem-bullet__icon.rem-bullet--all-children-visible {
              border: 2px solid var(--bullet-folder) !important;
              background-color: transparent;
              height: 7px !important;
              width: 7px !important;
              border-radius: 3px;
            }

            .folder.small.icon.rem-bullet__icon.rem-bullet--hidden-children {
              border: 2px solid var(--bullet-folder) !important;
              background-color: var(--bullet-folder);
              height: 7px !important;
              width: 7px !important;
              border-radius: 3px;
            }

            .folder.small.icon.rem-bullet__icon.rem-bullet--hidden-children::before,
            .folder.small.icon.rem-bullet__icon.rem-bullet--all-children-visible::before {
              display: none;
            }

            /* Concept Rem type Bullet */
            .rem-container--concept-rem-type
              .rem-bullet__container
              .rem-bullet.rem-bullet--all-children-visible {
              border: 2px solid var(--bullet-concept) !important;
              background-color: transparent;
              height: 7px !important;
              width: 7px !important;
            }

            .rem-container--concept-rem-type
              .rem-bullet__container
              .rem-bullet.rem-bullet--hidden-children {
              border: 2px solid var(--bullet-concept) !important;
              background-color: var(--bullet-concept);
              height: 7px !important;
              width: 7px !important;
            }

            /* Descriptor Rem type Bullet */
            .rem-container--descriptor-rem-type
              .rem-bullet__container
              .rem-bullet.rem-bullet--all-children-visible {
              border: 2px solid var(--bullet-descriptor) !important;
              background-color: transparent;
              height: 7px !important;
              width: 7px !important;
            }

            .rem-container--descriptor-rem-type
              .rem-bullet__container
              .rem-bullet.rem-bullet--hidden-children {
              border: 2px solid var(--bullet-descriptor) !important;
              background-color: var(--bullet-descriptor);
              height: 7px !important;
              width: 7px !important;
            }

            /* Bottom bar */
            .multiple-windows--one-pane #hierarchy-editor-toolbar-container {
              width: 100vw !important;
              left: 12px;
              height: 40px;
              border-top: 1px solid var(--border-c);
            }

            .paddingPage
              .multiple-windows--one-pane
              .hierarchy-editor-toolbar-container--opened
              #hierarchy-editor-toolbar {
              max-width: 55vw !important;
              margin-left: auto;
              margin-right: auto;
              border: none;
              filter: grayscale(100%);
              opacity: 0.6;
            }

            .paddingPage
              .multiple-windows--one-pane
              #hierarchy-editor-toolbar-container
              #hierarchy-editor__add-to-portal
              #hierarchy-editor__add-to-portal__inner {
              bottom: 0px;
              right: 19vw;
              width: 250px;
            }

            .page--no-padding
              .multiple-windows--one-pane
              .hierarchy-editor-toolbar-container--opened
              #hierarchy-editor-toolbar {
              max-width: 40vw !important;
              margin-left: auto;
              margin-right: auto;
              border: none;
              filter: grayscale(100%);
              opacity: 0.6;
            }

            .page--no-padding
              .multiple-windows--one-pane
              #hierarchy-editor-toolbar-container
              #hierarchy-editor__add-to-portal
              #hierarchy-editor__add-to-portal__inner {
              bottom: 0px;
              right: 12vw;
              width: 250px;
            }

            .small-window-page
              .multiple-windows--one-pane
              .hierarchy-editor-toolbar-container--opened
              #hierarchy-editor-toolbar {
              margin-left: 5vw;
            }

            .small-window-page
              .multiple-windows--one-pane
              #hierarchy-editor-toolbar-container
              #hierarchy-editor__add-to-portal
              #hierarchy-editor__add-to-portal__inner {
              bottom: 0px;
              right: 1vw;
              width: 200px;
            }

            .multiple-windows--one-pane
              #hierarchy-editor-toolbar-container
              #hierarchy-editor__add-to-portal
              .rich-text-editor {
              border: none;
              background-color: var(--soft-background-c);
              font-size: 11px;
            }

            .multiple-windows--two-panes #hierarchy-editor-toolbar-container {
              height: 40px;
              border-top: 1px solid var(--border-c);
            }

            .paddingPage
              .multiple-windows--two-panes
              .hierarchy-editor-toolbar-container--opened
              #hierarchy-editor-toolbar {
              max-width: 45vw !important;
              margin-left: auto;
              margin-right: auto;
              border: none;
              filter: grayscale(100%);
              opacity: 0.6;
            }

            .paddingPage
              .multiple-windows--two-panes
              #hierarchy-editor-toolbar-container
              #hierarchy-editor__add-to-portal
              #hierarchy-editor__add-to-portal__inner {
              bottom: 0px;
              width: 250px;
            }

            .page--no-padding
              .multiple-windows--two-panes
              .hierarchy-editor-toolbar-container--opened
              #hierarchy-editor-toolbar {
              max-width: 40vw !important;
              margin-left: auto;
              margin-right: auto;
              border: none;
              filter: grayscale(100%);
              opacity: 0.6;
            }

            .page--no-padding
              .multiple-windows--two-panes
              #hierarchy-editor-toolbar-container
              #hierarchy-editor__add-to-portal
              #hierarchy-editor__add-to-portal__inner {
              bottom: 0px;
              width: 250px;
            }

            .multiple-windows--two-panes
              #hierarchy-editor-toolbar-container
              #hierarchy-editor__add-to-portal
              .rich-text-editor {
              border: none;
              background-color: var(--soft-background-c);
              font-size: 11px;
            }

            .search-results #search-results__list,
            #hierarchy-editor-toolbar-container
              #hierarchy-editor__add-to-portal
              .search-results {
              z-index: 3;
              background-color: white;
              border: 1px solid var(--border-c) !important;
              border-radius: 5px;
              box-shadow: rgba(200, 200, 200, 0.1) 0px 0px 0px 1px,
                rgba(200, 200, 200, 0.2) 0px 0px 6px, rgba(200, 200, 200, 0.5) 0px 0px 12px !important;
            }

            #hierarchy-editor-toolbar-container
              #hierarchy-editor__add-to-portal
              #hierarchy-editor__add-to-portal__inner {
              /* Fix click issue on Add to Portel search box. Some other element above probably stole the click events. */
              z-index: 5;
            }

            /* Help Button */
            #help-button,
            #help-button:hover {
              bottom: 60px;
              background-color: var(--main-blue-c);
              color: white;
              opacity: 0.85;
            }

            /* Rem References Links */
            .rem-reference-link {
              color: var(--reference-c, #b979cf);
              padding: 0px 2px;
              border: none !important;
            }

            .rem-reference-link:hover {
              background-color: transparent !important;
              border: none !important;
            }

            .rem-reference--highlighted {
              box-shadow: none;
            }

            .rem-indented-indicator {
              color: var(--reference-c, #b979cf);
              vertical-align: text-bottom;
            }

            /* 2 docs view */
            #multiple-windows .multiple-windows__document {
              border-color: var(--border-c);
            }

            /* Portals */
            .rem.portal-rem--blue.portalRem {
              background-color: transparent !important;
              border: none !important;
              box-shadow: none !important;
            }

            #hierarchy-editor .portal-rem .portal-rem-top {
              border-top: 2px solid transparent;
              background-color: transparent;
            }

            #hierarchy-editor .portal-rem .portal-rem-top:hover {
              cursor: pointer;
            }

            #hierarchy-editor .portal-rem--selected .portal-rem-top {
              border: 1px solid var(--soft-blue-c) !important;
              background-color: var(--soft-blue-c);
              height: 0px;
              border-radius: 10px;
              margin-right: 15px;
            }

            #hierarchy-editor .portal-rem--selected {
              border: none !important;
            }

            #show-embedded-search-button {
              padding: 4px;
              margin-right: 0;
              margin-top: 4px;
              margin-left: -6px;
              border: none;
            }

            .embeddedSearch i.search.icon {
              margin-top: -4px;
              margin-right: 10px;
            }

            #show-embedded-search-button i.caret.down.icon {
              opacity: 0.5;
            }

            #hierarchy-editor .portal-rem--blue {
              border-color: transparent;
            }

            #hierarchy-editor .portal-rem-top--embedded-search-top {
              border-top-style: none !important;
            }

            i.refresh.icon {
              opacity: 0.5;
              margin-top: -5px;
              padding-top: 0px !important;
            }

            #show-embedded-search-button
              #show-embedded-search-button__delete-button
              i.icon {
              color: #aaa;
            }

            i.refresh.icon:hover {
              opacity: 0.85;
            }

            #show-embedded-search-button {
              font-size: 12px;
              text-transform: uppercase;
              letter-spacing: 0.1em;
            }

            #show-embedded-search-button > b {
              display: none;
            }

            .embeddedSearch {
              border-radius: 0.4em;
              border: 1px solid var(--soft-background-c);
              background-color: var(--soft-background-c);
              text-decoration: none;
              padding: 5px 5px 5px 10px;
              margin-left: 11px;
              margin-bottom: 8px;
              margin-top: -10px;
            }

            #hierarchy-editor .portal-rem--embedded-search {
              background-color: transparent !important;
              border: none !important;
              box-shadow: none !important;
            }

            #hierarchy-editor .search-portal-tree-node {
              margin-left: 4px;
              background-color: transparent;
              margin-right: 25px;
              border: 1px solid var(--border-c) !important;
              box-shadow: none;
              border-radius: 12px;
            }

            #hierarchy-editor
              .rem-container__top-level-spacer
              .rem-container__top-level-spacer__inner {
              display: none;
            }

            #hierarchy-editor .rem-container__top-level-spacer {
              display: none;
            }

            #Hierarchy-editor .HierarchyEditorAfterPortal {
              border: 1px solid var(--border-c) !important;
              box-shadow: none;
              border-radius: 5px;
              background-color: white;
            }

            #hierarchy-editor .rem-container--not-included-in-document-scope,
            #hierarchy-editor .notIncludedInDocumentScope .notIncludedAncestorClickable {
              text-decoration: none;
              color: #bbb;
            }

            #hierarchy-editor .rem-container--not-included-in-document-scope .join-arrow {
              font-size: 17px;
              color: grey;
            }

            #hierarchy-editor .isSearchResult {
              background-color: var(--soft-background-c);
              border: 1px solid var(--soft-background-c);
              padding: 5px 5px 5px 14px;
              border-radius: 5px;
              margin: 5px;
            }

            .isSearchResult .rem-bullet__container {
              margin-left: 10px;
              padding-top: 0.35em;
            }

            .isSearchResult .rem-bullet__container i {
              margin-left: 3px;
              padding-top: 0.6em;
            }

            .isSearchResult .rem-header--3,
            .isSearchResult .rem-header--2,
            .isSearchResult .rem-header--1 {
              background-color: transparent;
            }

            .search-portal-tree-node > .tree-node-container {
              margin-left: 10px;
            }

            .searchKeywordHighlight {
              background-color: transparent;
            }

            #hierarchy-editor .portal-tree-node {
              /* portal (not search) */
              background-color: transparent;
              border: 1px solid var(--border-c) !important;
              box-shadow: none;
              border-radius: 12px;
              padding-bottom: 10px;
              margin-left: 3px;
              padding-left: 20px !important;
              margin-right: 20px;
            }

            .import-all-contents-button__container {
              margin-top: 8px;
            }

            .ImportAllContentsButton {
              opacity: 0.5;
            }

            .ImportAllContentsButton:hover {
              color: grey;
              opacity: 0.8;
              font-weight: var(--focus-font-weight);
            }

            #hierarchy-editor .remChildren .ImportAllContentsButton {
              float: none;
              text-align: right;
            }

            #hierarchy-editor .hierarchy-editor__after-portal,
            #hierarchy-editor .indented-hierarchy-editor-rem--after-portal-embedded-search {
              border: none;
            }

            /* Rems Blocks */
            #hierarchy-editor .TreeNode {
              border-left: 1px solid var(--border-c);
            }

            #hierarchy-editor .TreeNodeListItems {
              border-left: 3px solid var(--border-c) !important;
            }

            #hierarchy-editor .rem-container--focused {
              background-color: transparent;
            }

            #hierarchy-editor .is-toolbar-previous-focus-rem {
              border: thin solid rgba(93, 161, 180, 0.4);
              box-shadow: none;
            }

            .selected-rem {
              background-color: rgba(93, 161, 180, 0.2);
              box-shadow: none;
            }

            /* Document Preview Popup */
            #document-hover-preview {
              box-shadow: 0 0 0 1px rgba(15, 15, 15, 0.05), 0 3px 6px rgba(15, 15, 15, 0.1),
                0 9px 24px rgba(15, 15, 15, 0.2);
              border: none;
              border-radius: 3px;
              margin: 10px;
              padding: 15px 20px !important;
            }

            #document-hover-preview #document-hover-preview__popup {
              padding-left: 5px;
            }

            /* Selected text Popup menu */
            .rich-text-editor__selected-text-menu {
              background-color: white;
              border: 1px solid var(--border-c);
              border-radius: 3px;
              box-shadow: rgba(200, 200, 200, 0.1) 0px 0px 0px 1px,
                rgba(200, 200, 200, 0.2) 0px 0px 6px, rgba(200, 200, 200, 0.5) 0px 0px 12px;
            }

            .rich-text-editor__selected-text-menu
              .rich-text-editor__selected-text-menu__divider {
              border: thin solid var(--border-c);
            }

            .rich-text-editor__selected-text-menu
              .rich-text-editor__selected-text-menu__search {
              padding-top: 7px;
              padding-bottom: 7px;
              border-top: thin solid var(--border-c);
              padding-left: 0px;
              padding-right: 0px;
            }

            .rich-text-editor__selected-text-menu .search-results {
              box-shadow: none;
              width: 400px;
              padding: 0px 7px;
            }

            .rich-text-editor__selected-text-menu .selected-text-menu__button:hover {
              background-color: white;
            }

            .rich-text-editor__selected-text-menu .selected-text-menu__button {
              opacity: 0.65;
            }

            .rich-text-editor__selected-text-menu .selected-text-menu__button--color {
              border: 1px solid var(--border-c);
            }

            /* Right Click popup */
            .right-click-menu {
              background-color: white;
              color: black;
              border: 1px solid var(--border-c) !important;
              border-radius: 3px;
              box-shadow: rgba(200, 200, 200, 0.1) 0px 0px 0px 1px,
                rgba(200, 200, 200, 0.2) 0px 0px 6px, rgba(200, 200, 200, 0.5) 0px 0px 12px !important;
            }

            /* Bottom Bar Popups */
            .ui.popup {
              background-color: white;
              border: 1px solid var(--border-c) !important;
              border-radius: 3px;
              box-shadow: rgba(200, 200, 200, 0.1) 0px 0px 0px 1px,
                rgba(200, 200, 200, 0.2) 0px 0px 6px, rgba(200, 200, 200, 0.5) 0px 0px 12px !important;
            }

            .hierarchy-editor-toolbar__menu
              .hierarchy-editor-toolbar__card-menu__view-as-card {
              border: none;
              box-shadow: none;
            }

            .hierarchy-editor-toolbar__menu .hierarchy-editor-toolbar__menu__item {
              border-bottom: none !important;
              border-top: thin solid var(--border-c) !important;
            }

            .hierarchy-editor-toolbar__menu
              .hierarchy-editor-toolbar__menu__item
              .hierarchy-editor-toolbar__menu__item__icon {
              opacity: 0.75;
              filter: grayscale(100%);
            }

            #BulletFormatIcons i {
              opacity: 0.75;
            }

            .hierarchy-editor-toolbar__menu
              .hierarchy-editor-toolbar__card-menu__view-as-card--on-right {
              background-color: white;
              border: 1px solid var(--border-c) !important;
              border-radius: 3px;
              box-shadow: rgba(200, 200, 200, 0.1) 0px 0px 0px 1px,
                rgba(200, 200, 200, 0.2) 0px 0px 6px, rgba(200, 200, 200, 0.5) 0px 0px 12px !important;
            }

            #QueueExample,
            #view-as-card #view-as-card__cards #view-as-card__card .spacedRepetition {
              background-color: white;
              border: 1px solid var(--border-c) !important;
              border-radius: 10px;
              box-shadow: none !important;
            }

            .ui.popup .toolbar-button,
            .ui.popup #BulletFormatIcons .icon {
              border: 1px soild var(--border-c) !important;
            }

            .popup .toolbar-button--selected {
              border: 1px solid var(--border-c) !important;
              box-shadow: rgba(200, 200, 200, 0.1) 0px 0px 0px 1px,
                rgba(200, 200, 200, 0.2) 0px 0px 6px, rgba(200, 200, 200, 0.5) 0px 0px 12px !important;
            }

            /* Ctrl + f popup */

            #hierarchy-editor__ctrl-f {
              margin-top: 5px;
              border-radius: 5px;
              border: 1px solid var(--border-c) !important;
              box-shadow: rgba(200, 200, 200, 0.1) 0px 0px 0px 1px,
                rgba(200, 200, 200, 0.2) 0px 0px 6px, rgba(200, 200, 200, 0.5) 0px 0px 12px !important;
            }

            #hierarchy-editor #hierarchy-editor-list__sticky-top__container {
              z-index: 5;
            }

            /* Latex */
            .katex {
              font-size: 18px !important;
              border-radius: 4px;
              padding: 0px 7px;
            }

            .LatexNodeFocused {
              border: 1px solid var(--border-c);
              border-radius: 4px;
              color: var(--font-c);
              padding: 0px 2px;
            }

            .LatexNode {
              text-decoration: none;
            }

            .LatexNode .latex-node__latex {
              border: none;
              margin-top: 5px;
              box-shadow: rgba(200, 200, 200, 0.1) 0px 0px 0px 1px,
                rgba(200, 200, 200, 0.2) 0px 0px 6px, rgba(200, 200, 200, 0.5) 0px 0px 12px;
              border-radius: 4px;
              padding: 2px 7px;
              background-color: white !important;
            }

            /* Link node */
            .LinkNode {
              text-decoration: none;
              color: var(--reference-c, #b979cf);
            }

            .link-node--focused {
              color: var(--reference-c, #b979cf);
              font-weight: 500;
            }

            /* Work in progress Rem */
            .workInProgressRem {
              padding: 0px;
              background-color: transparent;
            }

            .workInProgressRem > span::first-letter {
              visibility: hidden;
            }

            /* Flash Highlight */
            .flash {
              background-color: transparent !important;
              box-shadow: none;
              border: none;
            }

            /* Cards */
            /* Cloze */
            .cloze {
              background-color: #eee;
              padding: 0px 4px;
              text-decoration: none;
              border-radius: 4px;
              font-weight: 500;
            }

            /* Image Occlusion */
            .image-occlusion__toolbar > .button {
              font-size: 1em;
            }

            .image-occlusion__toolbar > .button > .icon {
              color: white !important;
            }

            .image-occlusion .image-occlusion__toolbar .image-occlusion__toolbar__dropdown {
              border: thin solid white;
              background-color: white;
              box-shadow: rgba(200, 200, 200, 0.1) 0px 0px 0px 1px,
                rgba(200, 200, 200, 0.2) 0px 0px 6px, rgba(200, 200, 200, 0.5) 0px 0px 24px;
              border-radius: 3px;
            }

            #clozeChangeDropdown #ClozeIdentifierInfo {
              color: var(--font-c);
            }

            #clozeChangeDropdown .ClozeIdentifierSelected {
              background-color: hsla(193, 37%, 54%, 0.3);
            }

            #clozeChangeDropdown #ClozeIdentifierOption {
              border: none;
            }

            #clozeChangeDropdown #ClozeIdentifierOption:hover {
              background-color: var(--hover-blue-c);
            }

            /* Queue Cards */
            .Queue {
              background-color: white;
              border: thin solid var(--border-c);
              border-radius: 4px;
              box-shadow: 0px 0px 3px 1px rgba(140, 167, 176, 0.25);
            }

            .Queue #queue__title {
              background-color: var(--soft-blue-c);
              box-shadow: 0px 1px 8px -2px #ccc;
              color: var(--reference-c, #b979cf);
              border-radius: 3px;
            }

            .Queue #QueueBadge,
            .Queue #queue__badge {
              color: white;
              margin-left: 5px;
              padding: 2px 7px;
              border-radius: 7px;
              background-color: var(--main-blue-c);
              border: 1px solid var(--main-blue-c);
              box-shadow: 0px 0px 4px 1px #eee;
              font-size: 12px;
            }

            .Queue #queue__title #QueueStreakIndicator {
              color: var(--main-blue-c);
              letter-spacing: 500;
            }

            .Queue #queue__progress-bar {
              background-color: var(--main-blue-c) !important;
            }

            .spacedRepetition
              .spaced-repetition__prompt
              .indented-rem
              .rem-bullet__document {
              border-radius: 3px;
              display: inline-block;
              padding: 4px;
            }

            .spacedRepetition .spaced-repetition__prompt {
              font-size: 15px;
              line-height: 1.4;
            }

            .spacedRepetition .spaced-repetition__prompt .bold {
              font-weight: 400;
            }

            .spacedRepetition .spacedRepetitionAnswer {
              border-color: var(--border-c);
            }

            .queue--desktop {
              box-shadow: 0px 0px 1px 10px white;
            }

            #ArticleQueue .QueueFocused {
              box-shadow: none;
            }

            .spacedRepetition .spaced-repetition__prompt .indented-rem .rem-bulletDocument {
              color: var(--hover-blue-c);
              font-size: 13px;
              margin-bottom: 5px;
              font-weight: 500;
              background-color: var(--soft-background-c);
            }

            .spacedRepetition .fill-in-the-blank {
              color: var(--soft-blue-c);
              border: none;
            }

            .spacedRepetition .spaced-repetition__bottom {
              background-color: var(--soft-background-c);
              font-weight: 500;
              font-size: 13px;
            }

            .spacedRepetition .spaced-repetition__reveal {
              background-color: var(--soft-background-c);
            }

            .spacedRepetition
              .spaced-repetition__prompt
              .indented-rem
              .rem-bullet__document
              i.icon {
              display: none;
            }

            .spacedRepetition .fill-in-the-blank {
              color: var(--main-blue-c);
            }

            .queue__buttons {
              background-color: var(--soft-background-c);
            }

            .spacedRepetition .queue__response-button--big[data-tip*="(1/4)"] > img {
              display: none;
            }
            .spacedRepetition .queue__response-button--big[data-tip*="(2/4)"] > img {
              display: none;
            }
            .spacedRepetition .queue__response-button--big[data-tip*="(3/4)"] > img {
              display: none;
            }
            .spacedRepetition .queue__response-button--big[data-tip*="(4/4)"] > img {
              display: none;
            }
            .spacedRepetition .queue__response-button--big[data-tip*="(1/4)"]:before {
              content: "☹️";
            }
            .spacedRepetition .queue__response-button--big[data-tip*="(2/4)"]:before {
              content: "😕";
            }
            .spacedRepetition .queue__response-button--big[data-tip*="(3/4)"]:before {
              content: "🙂";
            }
            .spacedRepetition .queue__response-button--big[data-tip*="(4/4)"]:before {
              content: "😊";
            }

            #leech-card #leech-card__header i.frown.outline.icon:before {
              display: none;
            }

            #leech-card #leech-card__header i.frown.outline.icon:before {
              content: "☹️";
            }

            #leech-card #leech-card__header {
              margin: 20px;
              font-weight: 500;
            }

            #leech-card #leech-card__contents {
              border: 1px solid var(--soft-background-c);
              border-radius: 3px;
              box-shadow: rgba(200, 200, 200, 0.1) 0px 0px 0px 1px,
                rgba(200, 200, 200, 0.2) 0px 0px 6px, rgba(200, 200, 200, 0.5) 0px 0px 24px;
            }

            #leech-card #leech-card__fixes .LeechAction,
            #leech-card #leech-card__fixes ul li {
              text-decoration: none;
              color: var(--hover-blue-c);
              font-weight: 400;
            }

            #leech-card #leech-card__fixes .LeechAction:hover {
              text-decoration: none;
              color: var(--hover-blue-c);
              font-weight: 500;
            }

            #leech-card .leech-card__bottom {
              background-color: var(--soft-background-c);
              color: var(--hover-blue-c);
              font-weight: 500;
              font-size: 13px;
            }

            .queue__response-button:hover {
              font-weight: 700;
              border-radius: 0px;
            }

            #milestone .daily-checkpoint {
              color: var(--hover-blue-c) !important;
            }

            #milestone .badge {
              border: 1px solid var(--soft-background-c);
              border-radius: 3px;
              box-shadow: rgba(200, 200, 200, 0.1) 0px 0px 0px 1px,
                rgba(200, 200, 200, 0.2) 0px 0px 6px, rgba(200, 200, 200, 0.5) 0px 0px 24px;
            }

            .queue__response-button,
            .accuracy-item {
              background-color: var(--soft-background-c);
              color: var(--font-c);
              font-weight: 500;
            }

            .queue__response-button:hover .queue__response-button__next-time {
              color: white;
            }

            .queue__response-button:hover,
            .accuracy-item:hover {
              background-color: var(--hover-blue-c);
              font-weight: 700;
              opacity: 0.65;
            }

            #milestone h1 {
              color: var(--hover-blue-c);
              font-weight: 600;
            }

            .Queue .queue__no-items .success {
              font-weight: 600;
              color: var(--hover-blue-c);
              padding-bottom: 20px;
              font-size: 15px;
            }

            #document-sidebar__link__queue-indicator {
              font-size: 12px;
            }

            #document-sidebar__link__queue-indicator i.star.icon:after {
              padding-right: 2px;
            }

            #document-sidebar__link__queue-indicator i.star.icon {
              color: white;
              padding-left: 7px;
              padding-right: 2px;
            }

            .queue__streak-indicator i.fire.icon {
              color: white;
            }

            .QueueDesktop .queue__title .queue__streak-indicator i.fire.icon {
              color: var(--main-blue-c) !important;
            }

            .queue__streak-indicator {
              align-items: baseline !important;
            }

            .black-out--enable {
              background-color: white;
            }

            .addListItemButton {
              border: none;
              border-radius: 3px;
              background-color: var(--soft-background-c);
              padding: 1px 7px;
              color: #888;
            }

            #QueueCollapsed {
              background-color: var(--soft-background-c);
              color: #aaa;
            }

            #QueueCollapsed #QueueCollapsedSmall {
              font-size: 13px;
            }

            #hierarchy-editor__embedded-queue-mode-toggle {
              color: #888 !important;
              margin-bottom: 5px !important;
            }

            #hierarchy-editor__embedded-queue-mode-toggle:hover {
              color: var(--font-background-c) !important;
            }

            /* Buttons */
            .ui.button {
              background: var(--main-blue-c);
              color: white;
            }

            .ui.button:hover {
              background: var(--hover-blue-c);
              color: white;
            }

            .ui.button i.add.icon {
              color: white;
            }
            /* } */
            ```
    - ## Customization
        ```css
        :root {
          --main-blue-c: #1d89e4;
          --hover-blue-c: rgb(25, 122, 208);
          --soft-blue-c: #d1e6f7;

          --font-c: black;
          --font-background-c: gray;

          --border-c: #eee;

          --soft-background-c: #f9f9f9;

          --bullet-main: #aaa;
          --bullet-doc: #81d5ed;
          --bullet-folder: #7172fc;
          --bullet-concept: #adcb2a;
          --bullet-descriptor: #f9c866;

          --focus-font-weight: 500;

          /* Highlight Colors */
          --highlight-red-c: #ffc7c7;
          --highlight-orange-c: #ffd599;
          --highlight-yellow-c: #fef49d;
          --highlight-green-c: #d7e985;
          --highlight-purple-c: #e4b1eb;
          --highlight-blue-c: #afd9fb;

          /* Linked Rems Color */
          --reference-c: #b979cf;
          /* Quote Background Color */
          --quote-background-c: #ecf3f6;

          /* Header size */  
          /* --header-1-font-size: 18px;
          --header-1-font-weight: 500;
          --header-2-font-size: 16px;
          --header-2-font-weight: 600;
          --header-3-font-size: 15px;
          --header-3-font-weight: 500;
  
          --header-1-margin-top: 8px;
          --header-2-margin-top: 5px;
          --header-3-margin-top: 3px; */

          /* === Font === */
          /* Chose one of the following fonts */
          /* --font-body: "Open Sans, sans-serif"; */
          /* --font-body: "Courier New, Courier, monospace"; */
          /* --font-body: "Century Gothic, sans-serif"; */
          /* --font-body: "Comic Sans MS, Comic Sans, cursive"; */
          /* --font-body: "Inter, sans-serif"; */
          /* --font-body: "Times, Times New Roman, serif"; */
          /* --font-body: "Arial, sans-serif"; */
          /* --font-body: "Open Sans, sans-serif"; */

          /* Or import a web font, see below for an @import statement. */
          /* --font-body: "Lato"; */
        }
        /* Import a web font here. */
        /* @import url("https://fonts.googleapis.com/css2?family=Lato&display=swap"); */
        ```
```
- 
