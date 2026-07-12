It is a way to handle continue flow of data, instead of loading the entire data into memory, streams let you process data chunk by chunk as it arrives.

Types of streams:
1. Readable streams
2. Writable streams
3. Duplex streams (for both reading and writing)
4. Transform streams

How streams is related to events
streams are built on top of events (it extends events class) like it can emits various events.
1. data - fires when the chunk of data is available.
2. end - fires when no more data is available.
3. error - fires if something goes wrong.
4. finish - fires when all data is flushed into writable stream.

Some advantages: 
1. memory efficient (as it didn't load the entire file for processing)
2. faster (as is process data on its arrival)
3. scalable (as with the help of this we can handle large data sources)