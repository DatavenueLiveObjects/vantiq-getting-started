# Vantiq & Live Objects Tutorial Introduction

This tutorial will go through the development, with Vantiq solution, of a **real-time business application** using IoT data coming from Live Objects, and enabling **human-to-machine collaboration**


## Introduction

The tutorial is divided in 2 parts:
> 2. VANTIQ Simulator, Live Objects Data Generator Project: this goes through the development of a Vantiq application to **generate simulated data** from sensors and push that simulated data into Live Objects. The simulated sensors are temperature sensors.

>  3. VANTIQ Business Application, Temperature Control Project : this goes through the development of a **real-time business application**, using data coming from Live Objects, and enabling human –to-machine collaboration.

The business application monitors and controls cold storage rooms temperature, in which refrigerated products are stored.

The temperature in the rooms has to stay below -19°C.  
State of the room can be  
- Normal : temperature is below -19°C.  
- Risky : temperature is comprised between -19°C and -15°C.  
- Critical : Above -15°C  
  
If temperature gets above -15°C during more than a certain time, the application will trigger a collaboration to inform controllers that might be able to correct the problem rapidly.  
If the controllers are not able to correct the situation, a mail will be sent to the chief of service , to inform him that a problem occurred, was not resolved by the controller and the stock of products may be out of order.



## Vantiq Account

You first need to ask for a VANTIQ developer test account [https://info.vantiq.com/vantiq-self-service-developer-portal-request](https://info.vantiq.com/vantiq-self-service-developer-portal-request).

## Live Objects

- **Live Objects Account**

If you do not have a Live Objects account, you can get a 1 year free account on that page: [https://liveobjects.orange-business.com/#/request_account](https://liveobjects.orange-business.com/#/request_account).

- **API Key**

You need to create an API Key.  
Select “Configuration” Tab, then “Api Keys” section.  
Click on “ Add an api Key”.

You have to fill the Name, and select “Application” as Profile.  
Then click on Create. You will get your API key.  
_Important : you have to keep it, Live Objects won't display it again if you lose it._

This API Key will be used by the Vantiq data simulation application and the Vantiq business application.

- **FIFO**

You need to create a Fifo to connect for the MQTT connection between the Vantiq business application and Live Objects.  
Select “Configuration” Tab, then “Message Bus” section.  
In FIFO queues tab, Click on “Add”.  
You will have to fill a name , for example vantiqFifo.  
then click on Register


In Routing keys tab, click on “Add”.  
Fill the routing key filter with “~event.v1.data.new.#”, for the targetFifo you just created. (All data coming to LiveObjects will be forwarded on the Fifo).  
Then Click on “Create Binding”.
