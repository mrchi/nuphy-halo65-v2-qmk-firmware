# NuPhy Halo65 V2 QMK Firmware

## Build

本机没有 `qmk` 和 `arm-none-eabi-gcc`，用本地已拉取的 QMK CLI 容器编译：

```sh
docker run --rm -v "$PWD":/qmk_firmware -w /qmk_firmware ghcr.io/qmk/qmk_cli:latest \
  sh -c "git config --global --add safe.directory '*'; \
         /opt/uv/tools/qmk/bin/python3 -m pip install -q -r requirements.txt; \
         qmk compile -kb nuphy/halo65_v2/ansi -km via"
```

- `pip install` 那步不能省：容器是 `--rm`，镜像里缺 `appdirs`，且 PATH 里没有 `uv`（CI 靠 `setup-uv` 注入，手动跑只能直接用镜像自带的 `pip`）。
- 产物为仓库根目录和 `.build/` 下的 `nuphy_halo65_v2_ansi_via.bin`，均在 gitignore 内，不进版本库。

## Agent skills

### Issue tracker

Issues live as markdown files under `.scratch/<feature>/`. See `docs/agents/issue-tracker.md`.

### Triage labels

Use the five default triage labels. See `docs/agents/triage-labels.md`.

### Domain docs

Single-context layout: one `CONTEXT.md` + `docs/adr/` at the repo root. See `docs/agents/domain.md`.
