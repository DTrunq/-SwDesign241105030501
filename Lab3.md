# Subsystem context diagrams
Một số hệ thống con: BankSystem, PrintService, ProjectManagementDatabase subsystems.

  - Hệ thống con: BankSystem
![](https://www.planttext.com/api/plantuml/png/j991Ri8m44NtESKeAv28s4SHGfHMwgQgn0aSPw0HZXrvnYfHoycww95wXOu9e01bsImSnvx___F4Fr_VSsBbEJGcQPNUgWr2kb1s2wkE61juS9Pnnoby90c0Dee8NbNddJ5nAxxHGr7eyyTi9hKWptGAhNSQYKJGeENHMDRtqQSMKxzM6k4vXXspUXbxPMcD_YdOYaPAQnSiluIcH9_3YdrjDnDGJLpDOUb2QN3IYvJcsjcbOfGD6SSvB9mpgEmfj-SVH1O5XPBwkS3kkZFz_sCyDgrn7UAnEy8YOys2SDFgdZOkt_O-osONNSmX3OIKtYs-pes2jXBGWsPeLNnc6LnQ7_wSd93WlUQtQy4Vzb9n7HYhBWvsCARJRS4Aocw0VzyxwauYWTydSxHLlCg_0000__y30000)
  - Hệ thống con PrintService

![](https://www.planttext.com/api/plantuml/png/h5BBReCm4Bpp5IjEYLIKEq8ewkEGMoI-m35RWcAmvLtQe9Olww6Vr5-eJN2KXEPMNonxPcTcr_xv-buJ2yjTeo8Zv45K2F7MrYr3WVQjbWXFkcKySWmVKGGWbI22hUYjLif3VaSBMIRFXpntN71hjG9ZjKIYKR9kgyNI0OCNScUqhy8PR4Oms9qgZRzoBdAFyh30nYZT8sxA50fsKFK0PWAVaKMjA03B51wrLYZQO3GbllJ8Ckfsr1DZumCU-tFYV_TzcII2flD6DmaEbiDigCMOor_Ffvma-SsuKeWxGehlqcS1V8Kf1P-AhjMopoI1M_tnfOHaWlUQz_EYlrmSQMRiULSzZk8KlWYMiEil-fWuzte8LQwB8LfZM_el_0i00F__0m00)

- Hệ thống con PrintService, ProjectManagementDatabase subsystems.

![](https://www.planttext.com/api/plantuml/png/h591ReCm4BppYXMdve1oHmX5QYySAaNA2nQpIMa18-_I1hMyh8S-gL-eJO2Y9g6N-8BCZ6Tcn_x-_Dgme96cBBmQrGiU2FojqS-a11wnilkIAe4754oH2Uvr9NGK7zuz3q0Lo0nRR8qk2WUvBnc88ZLjujXomQxr6Wo9oUcL1eUaskkxbGKx9vPRPRD7HP0C-6-0oVyaTKc7ohhGBL6IXR2pS7LOXJ0ZZ3P3vgiEKSHDoYqBbL0RVMod0MxcwW3hOrrp6UMxipvtVGRt-xpW88YNMWh1RvZOltfs7iIHwmpbn5zGZJw2OA4ugzDV8IfXUClbwH-vFpbSrbcg7fqNqUkpkn95p9H1sixc6pWNPXiFsEawRqDLvjxw3m000F__0m00)

# Mapping Analysis Class to Design Element

| **Analysis Class**               | **Design Element**                |
|-----------------------------------|------------------------------------|
| PayrollController                 | PayrollController (control)       |
| IBankSystem                       | IBankSystem (interface)           |
| BankSystem                        | BankSystem (subsystem proxy)      |
| EmployeePayment                   | EmployeePayment (entity)          |
| IPrintService                     | IPrintService (interface)         |
| PrintService                      | PrintService (subsystem proxy)    |
| IProjectManagementDatabase        | IProjectManagementDatabase (interface) |
| ProjectManagementDatabase         | ProjectManagementDatabase (subsystem proxy) |
| ProjectInfo                       | ProjectInfo (entity)             |

# Mapping Design Element to Owning Package

| **Design Element**                | **Owning Package**                |
|------------------------------------|-----------------------------------|
| PayrollController                  | PayrollSystem.Control             |
| IBankSystem                        | PayrollSystem.Interfaces          |
| BankSystem                         | PayrollSystem.Subsystems          |
| EmployeePayment                    | PayrollSystem.Entities            |
| IPrintService                      | PayrollSystem.Interfaces          |
| PrintService                       | PayrollSystem.Subsystems          |
| IProjectManagementDatabase         | PayrollSystem.Interfaces          |
| ProjectManagementDatabase          | PayrollSystem.Subsystems          |
| ProjectInfo                        | PayrollSystem.Entities            |
#  Architectural Layers and Dependencies
![](https://www.planttext.com/api/plantuml/png/Z5DBRi8m4DrpYb7sS80gYe2s2oIGa3Z1O0RgajYHxLIrsfwiYnwfL-YOLE3yW2oIM7xlpPitzk_tpzGwDAugyb69ueW7WcIDtkWyXustZWgO6V4Y7GbN6KhWOpG2k40DML8EdTGAbkZ910Jm8tAq5lwb7hLouKi6qbIS5rd6qA-6uBooKX4pb_eWHLDIAaTcZu9WCKTrhEsrTzQ65nioRr9GTq-_SXyhL5ohODzFw72BbYB7pqMPQq_4pWE2_V9REj_ZDR1X9iJ9RhVtYqSMiTNMrl-bqU-rsZcaoF9Dw407z_4MQgzxEkfEQJpEuf3X0PBAaas6mOqcxe4FDH9nOmVfvsG2JKUIHtNYqWws_aHeHXaeRL-zfC5GQuKhLhjoxGFK4oNF9noQgvHkRY6OSeUNIl5GRuUA8gh9Ov-IseLh_mS00F__0m00)
