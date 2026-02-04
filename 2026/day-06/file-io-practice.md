# Day 06 – Linux Fundamentals: Read and Write Text Files
### Task
- Create a file named notes.txt
- Write 3 lines into the file using redirection (> and >>)
- Use cat to read the full file
- Use head and tail to read parts of the file
- Use tee once to write and display at the same time
- Keep it short (8–12 lines total in the file)
  ## command flow:
```bash
    1  ls
    2  touch notes.txt
    3  ls
    4  echo "This is the sample file created using touch command" > notes.txt
    5  echo "this is the second file added to the file " >> notes.txt
    6  cat notes.txt
    7  echo "This is the third line added to file using the tee command" | tee -a notes.txt
    8  cat notes.txt
    9  echo "this is the fourth line added to the file" > notes.txt
   10  cat "this is the fiveth line added to the file" > notes.txt
   11  cat notes.txt
   12  echo "this is the fiveth line added to the file" > notes.txt
   13  cat notes.txt
   14  vim notes.txt
   15  head -n 5 notes.txt
   16  tail -n 5 notes.txt
   17  history 
