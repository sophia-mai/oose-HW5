## Design Principles

The design follows the Dependency Inversion Principle (DIP) because the Client depends on the FormatUtility interface rather than directly depending on the concrete PDFUtility class. This means the high-level Client does not need to know the details of how the tax report is converted into a particular format. For example, another implementation of FormatUtility could potentially be introduced later for a different format. The Client could continue interacting with the FormatUtility abstraction rather than becoming directly dependent on each concrete implementation.

The design also supports the Open/Closed Principle (OCP) because the formatting functionality can be extended without requiring major changes to the existing client code. For example, if another format such as HTML were needed, an HTMLUtility could implement FormatUtility. The Client could continue working through the same interface rather than being rewritten to depend directly on the new concrete class.

The design supports the Single Responsibility Principle (SRP) and high cohesion by separating the responsibilities of retrieving a tax report and formatting it. TaxReport is responsible for providing the tax report data, while PDFUtility is responsible for adapting that data into a PDF representation. This prevents one class from having to handle both the underlying tax report and every possible output format.

The design also promotes low coupling because the Client is not directly coupled to PDFUtility or TaxReport. Instead, it interacts with the FormatUtility abstraction. This reduces the amount of knowledge the client needs about the concrete implementation and makes it easier to replace or extend the formatting functionality.

## Design Pattern

The Adapter pattern has been applied in this design.

The existing TaxReport class provides the tax report through a method that returns a String:

```java
String getTaxReport(...)
```

However, the client wants to access the report through the FormatUtility interface, and PDFUtility provides the report as a PDF:

```java
PDF getTaxReport(...)
```

PDFUtility therefore acts as an adapter between the interface expected by the client and the existing TaxReport functionality. It uses TaxReport to obtain the report and converts or adapts that result into the PDF representation expected through FormatUtility.

This allows the existing TaxReport class to be reused without modifying it to directly support the client's desired PDF interface.
