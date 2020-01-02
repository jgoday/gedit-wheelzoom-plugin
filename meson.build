project(
  'gedit-wheelzoom-plugin', 'c',
  version: '3.35.2',
  meson_version: '>= 0.50'
)

gnome = import('gnome')

msgfmt_plugin_cmd = [
  find_program('msgfmt'),
  '--desktop',
  '--keyword=Name',
  '--keyword=Description',
  '--template=@INPUT@',
  '-d', 'po',
  '--output=@OUTPUT@'
]

# Paths
root_include_dir = include_directories('.')

srcdir = meson.current_source_dir()

libdir = join_paths(get_option('prefix'), get_option('libdir'))
datadir = join_paths(get_option('prefix'), get_option('datadir'))

pkglibdir = join_paths(libdir, 'gedit')
pkgdatadir = join_paths(datadir, 'gedit')

appstreamdir = join_paths(datadir, 'metainfo')
glibdir = join_paths(datadir, 'glib-2.0')
localedir = join_paths(datadir, 'locale')

libpeas_dep = dependency('libpeas-1.0', version: '>= 1.14.1')
gedit_dep = dependency('gedit', version: '>= 3.34.0')

appstream_util = find_program('appstream-util', required: false)

# config.h
config_h = configuration_data()
config_h.set_quoted('GETTEXT_PACKAGE', meson.project_name())

configure_file(
  output: 'config.h',
  configuration: config_h
)

subdir('src')
