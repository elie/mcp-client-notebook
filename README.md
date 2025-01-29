# MCP Client Notebook Test Prompts

This document contains sample prompts to test the MCP client notebook's ability to work with multiple tools and servers.

## Setup

Before running these test prompts, make sure:
1. The notebook is running
2. Both the filesystem and memory servers are started
3. There is a `filesystem-testing` directory with some test files

## Test Prompts

### 1. Multi-Tool Basic Test
```
What files are in the filesystem-testing directory and what's in memory?
```
This tests the ability to:
- Use the filesystem tool to list directory contents
- Use the memory tool to show current memory state
- Combine results from multiple tools

### 2. File Reading and Memory Test
```
Read the contents of hello.txt and store it in memory with the key 'hello_content'
```
This tests the ability to:
- Read a file from filesystem
- Store data in memory
- Chain multiple tool operations

### 3. Memory Operations Test
```
Store the text "This is a test" in memory with key "test_key" and then show what's in memory
```
This tests the ability to:
- Store data in memory
- Retrieve memory contents
- Perform sequential operations

### 4. File System Navigation Test
```
What directories are allowed in the filesystem server?
```
This tests the ability to:
- Query filesystem capabilities
- List allowed directories

### 5. Error Handling Test
```
Try to read a file called nonexistent.txt from the filesystem
```
This tests error handling when:
- Requesting non-existent files
- Handling tool errors properly

### 6. Combined Operation Test
```
Read hello.txt, store its contents in memory with key 'hello', then read bye.txt, store it with key 'bye', and show all memory contents
```
This tests:
- Multiple sequential tool uses
- Complex operations across tools
- State management between tools

## Expected Behavior

When these prompts are run, the client should:
1. Show Claude's thinking and tool use plans
2. Execute all necessary tools sequentially
3. Show tool results as they happen
4. Provide a final answer that combines all tool results

## Notes

- If Claude stops after using just one tool, there's a bug in the client implementation
- Each prompt should complete fully before asking for the next user input
- The memory server starts fresh each session, so state doesn't persist between notebook runs
