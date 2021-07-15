project('xf86-video-modesetting',
		'c',
		default_options: [
			'buildtype=debugoptimized',
			'c_std=gnu99'
		],
		version: '20.99.1',
		meson_version: '>= 0.50.0',
)

cc = meson.get_compiler('c')

xorg = dependency('xorg-server', version: '>= 1.6', required: true)
gbm_dep = dependency('gbm', version: '>= 10.2', required: false)

man_config = configuration_data()
man_config.set('appmansuffix', '1')
man_config.set('filemansuffix', '5')
man_config.set('drivermansuffix', '4')
man_config.set('miscmansuffix', '7')
man_config.set('xservername',
    cc.get_define('__XSERVERNAME__',
        prefix: '#include <xorg-server.h>',
        dependencies: xorg))
man_config.set('xconfigfile',
    cc.get_define('__XCONFIGFILE__',
        prefix: '#include <xorg-server.h>',
        dependencies: xorg))
man_config.set('vendorversion', '"@0@ @1@" "@2@"'.format(
        meson.project_name(),
        meson.project_version(),
        'X Version 11'))

subdir('src')
subdir('man')

