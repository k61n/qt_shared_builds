Alternative builds of Qt for dynamic linking for Windows arm64.

A github action from this repo can be used to checkout the release artifact.
This action will download and unpack a Windows arm64 release artifact, based on
the input of required qt version and one of supported compilers:
llvm1706/msvc2022.


      - name: Checkout shared Qt release
        id: qtsetup
        uses: k61n/qt_shared_builds/.github/actions/checkout@main
        with:
          version: 6.10.0
          compiler: <llvm1706|msvc2022>

The action will provide a `qtpath` variable containg the path to directory with
unpacked release artifact, you can use it like this:

    -DCMAKE_PREFIX_PATH=${{steps.qtsetup.outputs.qtpath}}