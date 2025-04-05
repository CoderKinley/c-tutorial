# 🧩 LeftMenuPanel Control Library (.NET 8 WinForms)

## 📋 Overview

**LeftMenuPanel** is a custom-built WinForms control developed using **.NET 8** that offers a modern, dynamic, and collapsible left-side menu panel with support for nested items. This component is designed to be reused across projects via a DLL or NuGet packaging and supports loading menu content from a JSON file at runtime.

This repository includes:
- A **WinForms Control Library** (`LeftMenuPanel.dll`)
- A **Demo WinForms Application** using the library
- JSON data file for dynamic menu loading
- Clean code structure adhering to **SOLID** principles
- Smooth UI/UX animations and interactions

---

## 🗃️ Folder Structure

```
/DeveloperAssessmentSolution
│
├── /LeftMenuPanelControlLib       ← Reusable WinForms Control Library
│   ├── /Controls                  ← UI controls (MenuPanel, MenuItemControl)
│   ├── /Core
│   │   ├── /Models               ← MenuItemModel and related models
│   │   ├── /Interfaces           ← IDataService, IThemeService, etc.
│   │   └── /Enums                ← MenuState, ThemeMode enums
│   ├── /Services                 ← MenuService, ThemeService
│   ├── /Infrastructure           ← JSONDataService (uses C1.AdoNet.JSON)
│   ├── /Resources                ← Icons, themes, etc.
│   ├── /Helpers                  ← Animation helpers, TooltipManager
│   ├── /Extensions               ← Custom extensions
│   └── LeftMenuPanelControlLib.csproj
│
├── /LeftMenuDemoApp              ← WinForms App for demonstration
│   ├── /Forms                    ← MainForm and demo views
│   ├── /Resources                ← menu.json, icons, assets
│   └── LeftMenuDemoApp.csproj
│
├── /tests                        ← Unit tests (optional)
│
├── README.md
└── DeveloperAssessmentSolution.sln
```

---

## ⚙️ Features

- ✅ Collapsible and expandable left-side panel
- ✅ Supports up to 2-level nested menu items (accordion behavior)
- ✅ Dynamically loads menu from a JSON file
- ✅ Hamburger icon toggles collapsed mode
- ✅ Responsive to window resize and resolution
- ✅ Smooth expand/collapse animations
- ✅ Hover effects on menu items
- ✅ Tooltips in collapsed view
- ✅ Active menu item highlight
- ✅ Dark mode toggle
- ✅ Vertical scrollbar when items overflow
- ✅ Graceful handling of 3+ level nesting (highlight + tooltip warning)

---

## 📂 JSON Structure

The JSON file must follow this structure:

```json
[
  {
    "title": "Dashboard",
    "icon": "icons/dashboard.png"
  },
  {
    "title": "Settings",
    "icon": "icons/settings.png",
    "items": [
      {
        "title": "General",
        "icon": "icons/general.png"
      },
      {
        "title": "Account",
        "icon": "icons/account.png",
        "items": [  // Invalid: more than 2 levels
          {
            "title": "Security",
            "icon": "icons/security.png"
          }
        ]
      }
    ]
  }
]
```

❗ If the nesting exceeds 2 levels:

- The parent will be visually highlighted.
- Tooltip: "This menu item has subitems and shall not be displayed."

## 🚀 How to Run

### ✅ Prerequisites

- Visual Studio 2022 or later
- .NET 8 SDK
- NuGet package: C1.AdoNet.JSON

### 🔧 Setup Instructions

1. **Clone Repository**

```bash
git clone https://bitbucket.org/your_username/leftmenupanel.git
cd leftmenupanel
```

2. **Open Solution**
   Open `DeveloperAssessmentSolution.sln` in Visual Studio.

3. **Set Startup Project**
   - Right-click `LeftMenuDemoApp` → Set as Startup Project.

4. **Ensure NuGet Package Is Installed**
   Run this in the NuGet Package Manager Console:

```bash
Install-Package C1.AdoNet.JSON
```

5. **Run Application**
   Press F5 or click Start Debugging.

## 🧠 Design & Implementation Choices

### SOLID Principles

- **Single Responsibility**: Services, models, UI, data access are separated.
- **Open/Closed**: Menu rendering supports extension via interfaces.
- **Liskov Substitution**: All service classes use interfaces.
- **Interface Segregation**: Data and theme logic are in separate interfaces.
- **Dependency Inversion**: Controls depend on abstractions like IDataService.

### Design Patterns

- **Strategy**: For data loading (JSON, other future sources)
- **Factory (optional)**: For creating control templates
- **Observer**: Menu reacts to state changes (expand/collapse)

### Animations & UI

- Menu expands/collapses with smooth transitions (via Timer + Width)
- Tooltips provide UX support when collapsed
- Dark mode toggles colors dynamically

### Data Binding

- JSON loaded into strongly-typed models
- Validated and bound to UI dynamically

## ❌ Known Limitations

- Does not currently support more than two nested levels (by design)
- No drag-and-drop menu editing
- Animation speed is fixed (configurable in future)

## 🧪 Testing (Optional)

- Place unit tests under /tests to verify services and menu parsing
- Suggested tools: xUnit, Moq for mocking services

## 👨‍💻 Developer Notes

- Collapsible width range: 200px → 60px
- Responsive layout uses Dock and FlowLayoutPanel
- UI assets (icons) are embedded in Resources
- Tooltip warnings implemented via ToolTip control
- JSON validation highlights issues during load

## 📤 Submission Instructions

1. Push to a BitBucket repository
2. Work on a branch called `development`
3. Commit with meaningful messages
4. Create Pull Request and add:
   - sonam.dendup@developertools.com
   - adriele.rosheger@developertools.com
5. Deadline: April 16, 2025

## 📎 License

This project is released under a custom assessment license. Usage restricted to evaluation.
