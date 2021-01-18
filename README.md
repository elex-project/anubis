# Project Anubis

Libraries to calculate Sun and Moon

- Moon phase
- Sun rise, sun set , transit
- Sun position

```java
SunRiseSunSet estimation = SunRiseSunSet
    .estimate(LocalDateTime.now(),
              new Parameters(35.198362, 129.053922));
log.info(estimation.toString());

SolarPosition solarPosition = SolarPosition
    .estimate(LocalDateTime.now(),
              new Parameters(35.1802563, 127.8292504));
log.info(solarPosition.toString());
```

```java
MoonPhaseCalculator2.Moon moonPahse = new MoonPhaseCalculator2().calculate(_now);
log.info(moonPahse.toString());

List<MoonPhaseCalculator2.MoonEvent> list2 = new MoonPhaseCalculator2()
    .getNextMoonEvents(_now, 5,
                       EnumSet.allOf(MoonPhaseCalculator2.MoonEventType.class));

for (MoonPhaseCalculator2.MoonEvent moonEvent : list2) {
    log.info(moonEvent.toString()+"\t" +moonEvent.getDate());
}
```

```java
SunriseSunsetCalculator calculator = new SunriseSunsetCalculator(
    Location.BUSAN, TimeZone.getTimeZone("GMT+9:00")
);
log.info(calculator.getOfficialSunriseForDate(_now));
log.info("시민박명: " + calculator.getCivilSunriseForDate(_now));
log.info("천문박명: " + calculator.getAstronomicalSunriseForDate(_now));
log.info("해상박명: " + calculator.getNauticalSunriseForDate(_now));
```

```java
int year = 2017, month = 11, day = 24, h = 19, m = 55, s = 0;
double obsLon = 129.053922, obsLat = 35.198362;
SunMoonCalculator smc = new SunMoonCalculator(year, month, day, h, m, s, obsLon, obsLat);

smc.calcSunAndMoon();

System.out.println("Sun");
System.out.println(" Az:      " + Math.toDegrees(smc.sunAz) + "º");
System.out.println(" El:      " + Math.toDegrees(smc.sunEl) + "º");
System.out.println(" Dist:    " + smc.sunDist + " AU");
System.out.println(" Rise:    " + SunMoonCalculator.getDateAsString(smc.sunRise, zone, null));
System.out.println(" Set:     " + SunMoonCalculator.getDateAsString(smc.sunSet, zone, null));
System.out.println(" Transit: " + SunMoonCalculator.getDateAsString(smc.sunTransit, zone, null) + " (max. elev. " + Math.toDegrees(smc.sunTransitElev) + "º)");
System.out.println("Moon");
System.out.println(" Az:      " + Math.toDegrees(smc.moonAz) + "º");
System.out.println(" El:      " + Math.toDegrees(smc.moonEl) + "º");
System.out.println(" Dist:    " + (smc.moonDist * SunMoonCalculator.AU) + " km");
System.out.println(" Age:     " + smc.moonAge + " days");
System.out.println(" Rise:    " + SunMoonCalculator.getDateAsString(smc.moonRise, zone, null));
System.out.println(" Set:     " + SunMoonCalculator.getDateAsString(smc.moonSet, zone, null));
System.out.println(" Transit: " + SunMoonCalculator.getDateAsString(smc.moonTransit, zone, null) + " (max. elev. " + Math.toDegrees(smc.moonTransitElev) + "º)");
```



-----

Copyright &copy; 2020 Elex. All Rights Reserved.
https://www.elex-project.com/