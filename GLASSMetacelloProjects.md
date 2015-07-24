### Fundamental projects ###
  * **[Core project](ConfigurationOfGsCore.md)** version 0.239.
    * The Core project is fundamental to the operation of GLASS and is always loaded.
  * **[Monticello project](ConfigurationOfGsMonticello.md)** version 0.237.
    * The Monticello project is fundamental to the operation of GLASS and is always loaded.
  * **Metacello project** version 1.0-beta.26.1.
    * The Metacello project is fundamental to the operation of GLASS. Metacello requires the Gofer which is managed with ConfigurationOfGofer.
### Optional projects ###
    * **[OB project](ConfigurationOfGsOB.md)** version 0.238.
      * The OB project is optional and provides the implementation for all of the OmniBrowser-based tools used in the GemTools client.
    * **Metacello Tools project** version 1.0-beta.26.1.
      * The Metacello Tools project is optional and provides OmniBrowser-based tool support for Metacello.
    * **Release Support project** version 0.236.
      * The Release Support project is optional and provides support for producing custom extents, via the bootstrapping process.
### Groups ###
    * **Dev group**.
      * The Dev group is the ‘default’ group and includes the Minimal group along with the Release Support, OB and Metacello Tools projects.
    * **Minimal group**.
      * The Minimal group includes all of the fundamental GLASS projects (Core, Monticello, and Metacello).