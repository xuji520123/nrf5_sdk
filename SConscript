# for module compiling
import os
from building import *

cwd = GetCurrentDir()

DriversDir = cwd
DeviceDrivers = [DriversDir + '/modules/nrfx/drivers/src/nrfx_clock.c']
DeviceDrivers += [DriversDir + '/integration/nrfx/legacy/nrf_drv_clock.c']

drv_path = [cwd]
drv_path += [cwd + '/modules/nrfx']
drv_path += [cwd + '/modules/nrfx/hal']
drv_path += [cwd + '/modules/nrfx/mdk']
drv_path += [cwd + '/modules/nrfx/drivers/include']
drv_path += [cwd + '/integration/nrfx']
drv_path += [cwd + '/integration/nrfx/legacy']
drv_path += [cwd + '/integration/nrfx']
drv_path += [cwd + '/components']
drv_path += [cwd + '/components/toolchain/arm']
drv_path += [cwd + '/components/toolchain/cmsis/include']
drv_path += [cwd + '/components/device']

drv_group = DefineGroup('nRF_Drivers', DeviceDrivers, depend = [''], CPPPATH = drv_path)

objs = [drv_group]

list = os.listdir(cwd)

for d in list:
    path = os.path.join(cwd, d)
    if os.path.isfile(os.path.join(path, 'SConscript')):
        objs = objs + SConscript(os.path.join(d, 'SConscript'))

Return('objs')
