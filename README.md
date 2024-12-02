## How it works
This project is an ongoing solution to modernizing inventory management that is a easy-to-use, $0, and open-source. The goal is to have a tool for anyone to use that enhances productivity and makes the job easier and more organized.

The basic assumed environment for using the tool is this.

``` mermaid
graph TD
    D[Delivery] --> A[Floor]
    D--Add---B[Backstock]
    B--Restock---A
```
### Receiving Deliveries
The inventory is added to when a delivery comes. In practice (using the terms employed here), this consists of a Count followed by an Add, or a cumulative Count.

### Restocking
Restocking occurs when something is needed on the floor:
1. (If count is not already stored,) Count relevant backstock.
2. From that set, enumerate what is needed on the floor.

What is needed on the floor will be subtracted from the backstock. If there is again backstock after stuff is put on a shelf, that will be another Add, like a delivery.

Most often, a full count of the backstock is not necessary. Therefore instead of doing a Count, do an Enumerate (no quantities). To subtract correctly from the backstock - i.e. to Restock - quantities will still be needed.

