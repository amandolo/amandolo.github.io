FROM node:lts-bullseye-slim as base
ENV PUPPETEER_SKIP_CHROMIUM_DOWNLOAD=1
ENV PUPPETEER_EXECUTABLE_PATH=/usr/bin/chromium-browser
ENV RESUME_PUPPETEER_NO_SANDBOX=1
COPY tools/rerun /bin/
RUN apt update -y && \
    apt install bc chromium inotify-tools -y && \
    npm install -g resume-cli yamljs --allow-root --unsafe-perm=true && \
    ln /usr/bin/chromium /usr/bin/chromium-browser && \
    chmod +x /bin/rerun


FROM base as build-base
ARG THEME
WORKDIR /resume
COPY ./src/ ./src/
RUN npm install jsonresume-theme-${THEME} && \
    npm install -g jsonresume-theme-${THEME}

FROM build-base as generate-base
ARG THEME
RUN mkdir out && \
    yaml2json -s -p src/resume.yaml && \
    resume export --resume src/resume.json --theme ${THEME} --format html out/resume.html && \
    resume export --resume src/resume.json --theme ${THEME} --format pdf out/resume.pdf

FROM scratch as generate
COPY --from=generate-base /resume/out/ ./

FROM build-base as server
ENV THEME=${THEME}
CMD rerun yaml2json -s -p src/resume.yaml & resume serve --resume src/resume.json --theme ${THEME}
