.. State Information Data exchange System documentation master file, created by
   sphinx-quickstart on Wed Jan 12 10:18:23 2022.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to State Information Data exchange System's documentation!
==================================================================



.. toctree::
   :maxdepth: 1

   EarningsVerification
   SeparationInformation
   SeparationInformationV2022
   FileAttachements
   QueueMessages
   Swagger
   ErrorCodes

`NASWA Sides <https://www.naswa.org/services/sides>`_

Libraries
=========

C# Nuget Packages (NetCore 3.1)
###############################
`Service Client <https://www.nuget.org/packages/SolidStateOps.StateInformationDataExchangeSystem.Service/>`_

`Queue Messages <https://www.nuget.org/packages/SolidStateOps.StateInformationDataExchangeSystem.Messages/>`_

Java Jar Packages
#################

*Repository*

.. code-block:: xml

   <repository>
   <id>SolidStateOps</id>
   <url>https://pkgs.dev.azure.com/solidStateOperations/034dccc2-479f-45e7-bcf0-b0d04a4a4576/_packaging/SolidStateOps/maven/v1</url>
   <releases>
      <enabled>true</enabled>
   </releases>
   <snapshots>
      <enabled>true</enabled>
   </snapshots>
   </repository>

*Latest LTS*

.. code-block:: xml

   <dependency>
      <groupId>com.solidstateops</groupId>
      <artifactId>sides-service</artifactId>
      <version>1.1.51.9</version>
   </dependency>

*1.6*

.. code-block:: xml

   <dependency>
      <groupId>com.solidstateops</groupId>
      <artifactId>sides-service-v1.6</artifactId>
      <version>1.1.51.12</version>
   </dependency>

.. raw:: html
   :file: images/DataFlow.svg
