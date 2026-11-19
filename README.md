# Selenium WebDriver UI Tests (C# / NUnit)

UI test automation project built with **Selenium WebDriver**, **C#** and **NUnit**,
written while learning QA automation (2021). It automates forms and drag-and-drop
interactions on [demoqa.com](https://demoqa.com) using the **Page Object Model**.

## Tech stack

| Area           | Tools                                                  |
| -------------- | ------------------------------------------------------ |
| Language       | C# (.NET Core 3.1)                                     |
| Test framework | NUnit 3                                                |
| Browser driver | Selenium WebDriver 3.141, ChromeDriver                 |
| Test data      | AutoFixture, factory classes                           |
| Patterns       | Page Object Model, Base Page / Base Test, extensions   |

## What is covered

| Area                  | Test class                          | Scenarios                                                                 |
| --------------------- | ----------------------------------- | ------------------------------------------------------------------------- |
| Practice form         | `Tests/Forms/PracticeFormsTests.cs` | Successful submission message; validation error when first name is empty  |
| Drag and drop         | `Tests/Interactions/Droppable.cs`   | Drop target changes colour; "Accept" tab only accepts the allowed element |
| Sortable list         | `Tests/Interactions/Sortable.cs`    | Reordering items by dragging up and down; list stays aligned              |
| Registration (legacy) | `SoftUniReg.cs`                     | Account registration and field validation on a demo e-shop                |

## Project structure

```
├── Pages/                  # Page objects
│   ├── BasePage.cs         # Shared driver, waits, navigation, scrolling
│   ├── HomePage/           # Each page is split into:
│   ├── Draggable/          #   *Elements.cs – locators
│   ├── SortablePage/       #   *Methods.cs  – user actions
│   └── DemoQAPage/         #   *Assert.cs   – reusable assertions
├── Tests/
│   ├── BaseTests.cs        # Driver and Actions set-up
│   ├── Forms/              # Form tests
│   └── Interactions/       # Drag-and-drop and sortable tests
├── Models/                 # Test data models
├── Factories/              # Test data builders
└── Utilities/Extensions/   # WebDriver extension methods (scroll, highlight)
```

Splitting every page into **Elements / Methods / Assert** keeps locators, actions and
checks in separate places, so a UI change only needs updating in one file.

## Running the tests

Requirements: .NET SDK and Google Chrome.

```bash
dotnet restore
dotnet test
```

Or open `LiveDemoSeleniumAdvanced.csproj` in Visual Studio and run the tests from Test Explorer.

> **Note:** this project targets .NET Core 3.1 and ChromeDriver 88 from 2021. Running it on a
> current machine requires updating `TargetFramework` and the Selenium / ChromeDriver packages.
> The legacy registration test uses `automationpractice.com`, which is no longer online.

## Related

- [skillo-playwright](https://github.com/martinab121/skillo-playwright) – current UI automation work with Playwright and TypeScript
