project (
    'remind',
    'c',
    default_options: [
        # does not compile even with c99:
        #'c_std=c11',
        # does not compile with the following either:
        #'warning_level=2',
        'werror=true',
    ],
)
add_project_arguments('-Wall', language: 'c')
add_project_arguments('-g',    language: 'c')
add_project_arguments('-O2',   language: 'c')
add_project_arguments('-Wstrict-prototypes', language: 'c')
add_project_arguments('-DHAVE_CONFIG_H',     language: 'c')

cc = meson.get_compiler('c')

executable (
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

executable (
    'rem2ps',
    'src/rem2ps.c',
    'src/dynbuf.c',
)
