project (
    'remind',
    'c',
)

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
    c_args : [
        '-Wno-error',
        '-g',
        '-O2',
        '-Wall',
        '-Wstrict-prototypes',
        '-DHAVE_CONFIG_H',
        '-I.',
        '-I.'
    ],
    link_args : ['-lm']
)

executable (
    'rem2ps',
    'src/rem2ps.c',
    'src/dynbuf.c',
    c_args : [
        '-Wno-error',
        '-g',
        '-O2',
        '-Wall',
        '-Wstrict-prototypes',
        '-DHAVE_CONFIG_H',
        '-I.',
        '-I.'
    ],
)
