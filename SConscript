import rtconfig
from building import *

# get current directory
cwd = GetCurrentDir()
path = [cwd + '/Include']

# The set of source files associated with this SConscript file.

if GetDepend(['SOC_HC32F334KA']):

    src = Split('''
    Device/HDSC/hc32f334/Source/system_hc32f334.c
    ''')

    if rtconfig.PLATFORM in ['gcc']:
        src += ['Device/HDSC/hc32f334/Source/GCC/startup_hc32f334.S']
    elif rtconfig.PLATFORM in ['armcc', 'armclang']:
        src += ['Device/HDSC/hc32f334/Source/ARM/startup_hc32f334.s']
    elif rtconfig.PLATFORM in ['iccarm']:
        src += ['Device/HDSC/hc32f334/Source/IAR/startup_hc32f334.s']

    path += [cwd + '/Device/HDSC/hc32f334/Include']

CPPDEFINES = ['USE_DDL_DRIVER']

group = DefineGroup('Libraries', src, depend = [''], CPPPATH = path, CPPDEFINES = CPPDEFINES)

Return('group')
