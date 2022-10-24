Documentation: https://www.ibm.com/docs/en/spectrum-lsf/10.1.0?topic=reference-command

- kill all: `bkill 0`
- kill all from queue regress: `bkill -q regress 0`
- request 'rhel7' machine: `-R ws70`
- request 'regress' queue: `-q regress`
- `bsub -q gui -Is xterm`: 
    - `xterm`: will open a new terminal in the lsf machine 
    - `-q gui`: as this requires graphical interface, we need gui queue
    - `-Is`: as this is interactive
- request full cpu & specific RAM: `-R "select[ws70 && fullcpu && mem>100000 && maxmem>200000]"` (here mem & maxmem values are in MB)
- send output to a file w/o sending log report of lsf:
    - syntax: `bsub -R ws70 -q regress -o /path/to/file -N "<command>"`
    - `-o`: will send output to given file path
    - `-N`: will send lsf report to mail instead of file 