- You should aim to use as few deps as possible. This ensures your build-order runs as fast as possible and doesn't get blocked unnecessarily.

- Timings should primarily be limited by just one thing: eco-level, age-status, or some dep. This ensures we don't delay it when it could be made sooner than expected.

- You can get items prior to meeting the age requirement. This can be used for reserving resources / pre-moving builders automatically.

- Should specify all military building / building dependency items to ensure they are built at the correct time.

- You should not have dependencies of farms; this is usually a design flaw. Instead ensure you have adequate deps for your farm items.

- For blacksmith researches you should use dependencies of unit classes rather than individual units.

- ri-horse-collar and ri-padded-archer-armor will be completely skipped for feudal-age if not included, so make sure you include them if desired

- Using drop/buy options can speed up item timings but worsnens your economy in the long run. Best to avoid using it unless important.