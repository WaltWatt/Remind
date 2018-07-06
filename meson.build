project(
    'remind',
    'c',
    version : '03.01.15',
    default_options: [
        # does not compile even with c99:
        #'c_std=c11',
        # does not compile with the following either:
        #'warning_level=2',
    ],
)
add_project_arguments('-Wall', language: 'c')
add_project_arguments('-g',    language: 'c')
add_project_arguments('-O2',   language: 'c')
add_project_arguments('-Wstrict-prototypes', language: 'c')
add_project_arguments('-DHAVE_CONFIG_H',     language: 'c')

cc = meson.get_compiler('c')

as_version = meson.project_version()
ver_arr = as_version.split('.')

as_major_version = ver_arr[0]
as_minor_version = ver_arr[1]
as_micro_version = ver_arr[2]

msg = '''

**********************
*                    *
* Configuring REMIND *
*                    *
**********************
'''

## Let's respect the Remind's authors
tm = target_machine.system()
if tm == 'darwin'
    msg += '''
Please don't use Apple products.  This script will continue in 30 seconds
if you insist on compiling Remind on Mac OS X.
'''
elif tm == 'cygwin'
    msg += '''
Please don't use Microsoft products.  This script will continue in 30
seconds if you insist on compiling Remind on Cygwin.
'''
endif
message(msg)
if tm == 'darwin' or tm == 'cygwin'
    ## Cannot make trap work!
    #run_command('trap', '\'echo Be patient...\'', 'INT', 'TERM')
    run_command('sleep', '30')
    #run_command('trap', '-', 'INT')
    #run_command('trap', '-', 'TERM')
endif

config = configuration_data()

### Check for header files
desc = 'Define if you have the <sys/time.h> header file'
val = cc.has_header('sys/file.h')
config.set('HAVE_SYS_FILE_H', val == true ? 1 : false, description: desc)

desc = 'Define if you have the <glob.h> header file'
val = cc.has_header('glob.h')
config.set('HAVE_GLOB_H', val == true ? 1 : false, description: desc)

desc = 'Define if you have the <wctype.h> header file'
val = cc.has_header('wctype.h')
config.set('HAVE_WCTYPE_H', val == true ? 1 : false, description: desc)

desc = 'Define if you have the <locale.h> header file'
val = cc.has_header('locale.h')
config.set('HAVE_LOCALE_H', val == true ? 1 : false, description: desc)

### Check for library functions
val = cc.has_function('setenv', prefix : '#include <stdlib.h>')
config.set('HAVE_SETENV', val == true ? 1 : false)

val = cc.has_function('unsetenv', prefix : '#include <stdlib.h>')
config.set('HAVE_UNSETENV', val == true ? 1 : false)

val = cc.has_function('glob', prefix : '#include <glob.h>')
config.set('HAVE_GLOB', val == true ? 1 : false)

val = cc.has_function('mbstowcs', prefix : '#include <stdlib.h>')
config.set('HAVE_MBSTOWCS', val == true ? 1 : false)

val = cc.has_function('setlocale', prefix : '#include <locale.h>')
config.set('HAVE_SETLOCALE', val == true ? 1 : false)

### Integer sizes
desc = 'The number of bytes in an unsigned short'
val = cc.sizeof('unsigned short', prefix : '#include <stdio.h>')
config.set('SIZEOF_UNSIGNED_SHORT', val, description: desc)

desc = 'The number of bytes in an unsigned int'
val = cc.sizeof('unsigned int', prefix : '#include <stdio.h>')
config.set('SIZEOF_UNSIGNED_INT', val, description: desc)

desc = 'The number of bytes in an unsigned long'
val = cc.sizeof('unsigned long', prefix : '#include <stdio.h>')
config.set('SIZEOF_UNSIGNED_LONG', val, description: desc)

configure_file(
    input  : 'src/config.h.in',
    output : 'config.h',
    configuration : config,
)

config_ver = configuration_data()
config_ver.set_quoted('VERSION', as_version)
configure_file(
    output : 'version.h',
    configuration : config_ver,
)

config_custom = configuration_data()
configure_file(
    input  : 'src/custom.h.in',
    output : 'custom.h',
    configuration : config_custom,
)

m_dep = cc.find_library('m', required : true)

executable(
    'remind',
    'src/main.c',
    'src/calendar.c',
    'src/dynbuf.c',
    'src/dorem.c',
    'src/dosubst.c',
    'src/expr.c',
    'src/files.c',
    'src/funcs.c',
    'src/globals.c',
    'src/hbcal.c',
    'src/init.c',
    'src/main.c',
    'src/md5.c',
    'src/moon.c',
    'src/omit.c',
    'src/queue.c',
    'src/sort.c',
    'src/token.c',
    'src/trigger.c',
    'src/userfns.c',
    'src/utils.c',
    'src/var.c',
    link_args : ['-lm']
)

executable(
    'rem2ps',
    'src/rem2ps.c',
    'src/dynbuf.c',
)
