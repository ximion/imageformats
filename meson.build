project('imageformats', 'd',
    meson_version: '>=0.46',
    license: 'BSL-1.0',
    version: '7.0.0'
)

project_soversion    = '0'

src_dir = include_directories('.')
pkgc = import('pkgconfig')

imageformats_src = [
    'imageformats/bmp.d',
    'imageformats/jpeg.d',
    'imageformats/package.d',
    'imageformats/png.d',
    'imageformats/tga.d'
]
install_subdir('imageformats/', install_dir: 'include/d/imageformats-d/')

imageformats_lib = library('imageformats-d',
        [imageformats_src],
        include_directories: [src_dir],
        install: true,
        version: meson.project_version(),
        soversion: project_soversion
)

pkgc.generate(name: 'imageformats-d',
              libraries: imageformats_lib,
              subdirs: 'd/imageformats-d/',
              version: meson.project_version(),
              description: 'Decoders for PNG, TGA, BMP, JPEG and encoders for PNG, TGA, BMP.'
)

# for use by others which embed this as subproject
imageformats_dep = declare_dependency(
    link_with: [imageformats_lib],
    include_directories: [src_dir]
)
