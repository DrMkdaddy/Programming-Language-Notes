This is standard boiler plate but I want to list out the features that the elixir language has. 
- Python-like syntax
- Easy Concurrency where individual modules or functions could be spawned as a sub-process and be able to communicate with its siblings very well. 
- It is built on-top of Erlang's BEAM VM allowing for
	- Fault Tolerance, Only the faulty process will fail, allowing the supervisor process to restart it. 
	- Compatibility with Erlang, they're both compiled down to the same bytecode. 
	- 
