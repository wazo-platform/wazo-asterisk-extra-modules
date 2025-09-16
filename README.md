# wazo-asterisk-extra-modules

Extra dependencies required by Asterisk for modules that are not loaded by default on Wazo

## Updating this package

If the dependencies of this package get outdated the following procedure will allow you to
find what are the required dependencies for Asterisk.

1. Modify the Asterisk packaging to include all of its modules

   In the Asterisk repository in debian/rules comment out all the -X in the
  `DEB_DH_SHLIBDEPS_ARGS_ALL` variable

2. Build your modified version of Asterisk using the instructions in the
   [Asterisk repo](https://github.com/wazo-platform/asterisk) README

3. Install your new version of Asterisk

4. Compare the dependencies between your new Asterisk and the one available on the wazo mirror

    ```sh
    apt show asterisk
    apt show asterisk/wazo-dev-bullseye
    ```

5. All dependencies that are in the `Depends` of the newly built Asterisk package but are
   not in the `Depends` of the Asterisk on the mirror must be added to this project's `Depends`
