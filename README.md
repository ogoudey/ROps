# Retail Operations

This project is an ongoing solution to modernizing inventory management that is a easy-to-use, $0, and open-source. The goal is to have a tool for anyone to use that enhances productivity and makes the job easier and more organized. It tries to quantify retail environments and help workers track a storefront's inventory.

So far it is _not_ easy to use for normal people, nor is it flawless, but it is a start. To address this, the next step would probably be to make a GUI corresponding to the Usage operations below. 

## Usage

### Setup
Open the python notebook and insert your API key. The rest of this section describes operations a user would do live, at work.

### Receiving Deliveries
The inventory is added to when a delivery comes. In practice (using the terms employed here), this consists of a Count followed by an Add, or a cumulative Count.

### Restocking
Restocking occurs when something is needed on the floor:
1. (If a count is not already stored,) Count relevant backstock.
2. From that set, enumerate what is needed on the floor.

What is needed on the floor will be subtracted from the backstock. If there is again backstock after stuff is put on a shelf, that will be another Add, like a delivery.

Most often, a full count of the backstock is not necessary. Therefore instead of doing a Count, do an Enumerate (no quantities). To subtract correctly from the backstock - i.e. to Restock - quantities will still be needed.

### Comments
In theory, performing a Count is not necessary, only accurate Adds and Restocks. Yet building inventory management up from nothing means we cannot assume we have overall numbers. Instead this chips at the whole by section and only at certain times.

Currently there is something slowing down GBoard in a .ipynb. Voice transcription gets fragmented. As a result testing this tool in the field has this barrier.

## How it Works
Behind the scenes, the system uses an LLM to perform operations on informally written lists of products. For example, `"two oranges and umm three pears"` are mapped to the dictionary `{"oranges": 2, "pears": 3}' in a Count operation above.

