THEME = actual

generate:
	rm -rf build
	docker build --target generate --build-arg THEME=$(THEME) -o build .
	
dev:
	rm -rf build
	docker build --target server --build-arg THEME=$(THEME) -t resume-server .
	docker run --rm -v ${PWD}/src/:/resume/src/ -p 4000:4000 -it --name resume-server resume-server
