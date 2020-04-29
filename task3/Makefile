all: partials collision

.PHONY: partials
partials: collide.c
	gcc -o collide collide.c
	head -c 4160 collide > pre.bin
	tail -c +4288 collide > suffix.bin
	md5collgen -p pre.bin -o prefix1.bin prefix2.bin

.PHONY: collision
collision: prefix1.bin prefix2.bin
	cat prefix1.bin suffix.bin > collide1
	cat prefix2.bin suffix.bin > collide2
	sudo chmod +x collide1 collide2

.PHONY: sum
sum: collide1 collide2
	md5sum collide1 collide2

.PHONY: clean
clean:
	rm -f collide collide1 collide2 *.bin
