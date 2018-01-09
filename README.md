(Modified from https://github.com/khaytsus/direwolf-init)

# trunk-recorder PPM calibration

Problem:  RTL-SDR sticks the PPM varies as the temperature changes, and decoding
P25 requires the PPM to be pretty close, probably within 2-3 or you'll have
issues decoding.

Solution:  Using a chosen frequency as a source, I use `rtl_power` to find the
best signal and then figure out what the correct PPM is based on that, and
use that new PPM.

Setup a cron job every hour to run `./get_ppm` which will run the
calibration script and update the trunk-recorder config file listed within
the script with the new PPM value.

Files:

 * `findppm.pl` - Perl script which determines the best PPM
 * `get_ppm` - Script which updates ppm

Edit `get_ppm` with the path to your config file, and the reference
frequencies / device IDs to use.
