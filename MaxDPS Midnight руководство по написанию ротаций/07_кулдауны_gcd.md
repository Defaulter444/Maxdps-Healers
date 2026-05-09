7. Кулдауны и GCD
Кулдаун — это характеристика способности, которая показывает, готова ли она к использованию, сколько времени осталось
до её восстановления, есть ли у неё заряды и как быстро они восстанавливаются.
Все выражения такого типа записываются в формате cooldown.способность.поле, где вместо слова способность нужно
подставить имя нужной способности в формате программы.
ВЫРАЖЕНИЕ ЧТО ВОЗВРАЩАЕТ ПРИМЕР
cooldown.способность.ready Способность готоваif=cooldown.mortal_strike.ready
cooldown.способность.up То же самое, что и .readyif=cooldown.execute.up
cooldown.способность.remains Оставшееся время кулдауна в
секундах
if=cooldown.avatar.remains<5
cooldown.способность.duration Полная длительность
кулдауна в секундах
if=fight_remains>cooldown.avatar.duration
cooldown.способность.charges Количество доступных
зарядов
if=cooldown.shield_slam.charges>=1
cooldown.способность.charges_fractionalДробное количество зарядов
с учётом восстановления
следующего
if=cooldown.shield_slam.charges_fractional>1.5
cooldown.способность.max_charges Максимальное количество
зарядов
if=cooldown.shield_slam.max_charges=2
cooldown.способность.full_recharge_timeВремя до полного
восстановления всех зарядов
if=cooldown.shield_slam.full_recharge_time<3
# Использовать Shield Slam, только если у него более 1 заряда
actions+=shield_slam,if=cooldown.shield_slam.charges>1
# Использовать Overpower, если до готовности Mortal Strike осталось больше 1 секунды
actions+=overpower,if=cooldown.mortal_strike.remains>1
# Использовать Avatar, только если цель проживет дольше полного оката кулдауна
actions+=avatar,if=target.time_to_die>cooldown.avatar.duration
GCD — глобальный кулдаун
Также в условиях можно использовать глобальный кулдаун — gcd. Для него поддерживаются те же основные поля, что и
для обычного кулдауна, например gcd.remains и gcd.duration. На практике такие проверки используются редко, но
иногда могут быть полезны в сложной логике ротации.