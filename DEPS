# This file is used to manage the dependencies of the Evita src repo. It is
# used by gclient to determine what version of each dependency to check out, and
# where.

vars = {
  'chromium_git': 'https://chromium.googlesource.com',
  'github.git': 'https://github.com',

  'buildtools_revision': '1f985091a586bb6e95872d4d876b7d7fc57850d6',
  'POGOProtos_revision': '04c90348e7adf91bcd0ce5bdfbc97ba369874328', # v2.1.0
  'protobuf_revision': 'cd315dcbadc02569e145bde16e3f66c2fbb08e31',
}

deps = {
  'src/buildtools':
    Var('chromium_git') + '/chromium/buildtools.git' + '@' +  Var('buildtools_revision'),

  'src/third_party/POGOProtos':
    Var('github.git') + '/AeonLucid/POGOProtos.git' + '@' + Var('POGOProtos_revision'),

  'src/third_party/protobuf':
    Var('github.git') + '/google/protobuf.git' + '@' + Var('protobuf_revision'),
}

hooks = [
  # Pull GN binaries. This needs to be before running GYP below.
  {
    'name': 'gn_win',
    'pattern': '.',
    'action': [ 'download_from_google_storage',
                '--no_resume',
                '--platform=win32',
                '--no_auth',
                '--bucket', 'chromium-gn',
                '-s', 'src/buildtools/win/gn.exe.sha1',
    ],
  },
  {
    'pattern': '.',
    'action': ['src\\build\\gn_pgo.cmd']
  },
]
