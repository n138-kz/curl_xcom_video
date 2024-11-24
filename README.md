# [curl_xcom_video](https://github.com/n138-kz/curl_xcom_video)

## Activity

[![GitHub repo license](https://img.shields.io/github/license/n138-kz/curl_xcom_video)](/LICENSE)
[![GitHub repo size](https://img.shields.io/github/repo-size/n138-kz/curl_xcom_video)](/../../)
[![GitHub repo file count](https://img.shields.io/github/directory-file-count/n138-kz/curl_xcom_video)](/../../)
[![GitHub code size in bytes](https://img.shields.io/github/languages/code-size/n138-kz/curl_xcom_video)](/../../)
[![GitHub last commit](https://img.shields.io/github/last-commit/n138-kz/curl_xcom_video)](/../../commits)
[![GitHub commit activity](https://img.shields.io/github/commit-activity/w/n138-kz/curl_xcom_video)](/../../commits)
[![GitHub commit activity](https://img.shields.io/github/commit-activity/t/n138-kz/curl_xcom_video)](/../../commits)
[![GitHub issues](https://img.shields.io/github/issues/n138-kz/curl_xcom_video)](/../../issues)
[![GitHub issues closed](https://img.shields.io/github/issues-closed/n138-kz/curl_xcom_video)](/../../issues)
[![GitHub pull requests closed](https://img.shields.io/github/issues-pr-closed/n138-kz/curl_xcom_video)](/../../pulls)
[![GitHub pull requests](https://img.shields.io/github/issues-pr/n138-kz/curl_xcom_video)](/../../pulls)
[![GitHub language count](https://img.shields.io/github/languages/count/n138-kz/curl_xcom_video)](/../../)
[![GitHub top language](https://img.shields.io/github/languages/top/n138-kz/curl_xcom_video)](/../../)

```bash
i=https://video.twimg.com/amplify_video/1697304568550330368/pl/720x720/aRhMM5nnY2j8e7Qr.m3u8
h=$(basename "$i" .m3u8)
if [ ! -d "${h}" ] ; then mkdir "${h}" && cd $_ ; else cd "${h}" ; fi
wget "${i}"
for i in $(cat ${h}.m3u8 | grep / | sed -e 's/"//g' | sed -e 's/^.*=//g'); do
	wget https://video.twimg.com${i}
done
for i in $(cat ${h}.m3u8 | grep / | sed -e 's/"//g' | sed -e 's/^.*=//g'); do
	file $(basename ${i})
done
cat ${h}.m3u8 | sed -e 's#/.*/##g' > ${h}_1.m3u8
ffmpeg -i ${h}_1.m3u8 -c copy -bsf:a aac_adtstoasc -y ${h}.mp4 && mv ${h}.mp4 ../

cd ..

```
