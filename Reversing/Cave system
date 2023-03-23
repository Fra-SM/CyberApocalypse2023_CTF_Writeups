# Cave system

Luckily, this time angr decided to do its job and get me through a mess of condition checks. The following is an example script we can use for solving this challenge:

```python
import angr
import claripy
from angr.storage.file import SimFileStream

TO_FIND = [0x101ab3]
TO_AVOID = [0x101abf]

STDIN_FD = 0
FLAG_LEN = 64
BASE_ADDR = 0x100000

proj = angr.Project('./cave', main_opts={'base_addr': BASE_ADDR})

flag_chars = [claripy.BVS('flag_%d' % i, 8) for i in range(FLAG_LEN)]
flag = claripy.Concat(*flag_chars + [claripy.BVV(b'\n')])

state = proj.factory.entry_state(
                        args = ['./cave'], 
                        stdin = SimFileStream(name = 'stdin', content = flag))

#only printable characters constraints
for c in flag_chars:
    state.solver.add(c >= ord('!'))
    state.solver.add(c <= ord('~'))

#known flag characters constraints
state.solver.add(flag_chars[0] == 'H')
state.solver.add(flag_chars[1] == 'T')
state.solver.add(flag_chars[2] == 'B')
state.solver.add(flag_chars[3] == '{')

simgr = proj.factory.simulation_manager(state)

simgr.explore(find=TO_FIND, avoid=TO_AVOID)

#if at least a valid state was found (=> problem is SAT)
if (len(simgr.found) > 0):
    #dump the input that was given to each found state (if many)
    for found in simgr.found:
        print(found.posix.dumps(STDIN_FD))
else:
    print('Not found!')
```

## HTB{H0p3_u_d1dn't_g3t_th15_by_h4nd,1t5_4_pr3tty_l0ng_fl4g!!!}