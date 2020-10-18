---
title: "Gmail Information Extraction: From Juicer to Crusher"
date: 2020-09-20 15:55:52
mathjax: true
tags:
---
读完今年的paper指标后想找点有趣的东西，在vldb上闲逛时找到了一篇关于改进Gmail处理B2C邮件系统的paper，部分思路跟至今没读完的Google News(~~我是真的毫无强迫症~~)相似所以读得很愉快，遂顺便读了关于原本系统的paper。
如同标题，原版叫Juicer，新版叫Crusher。Google的起名有时非常一言难尽。

<!-- more -->
笔记完全基于两篇paper：
- Anatomy of a Privacy-Safe Large-Scale Information Extraction System Over Email
- Online Template Induction for Machine Generated Emails

## Problem Statement
世界上>90%的邮件是机器生成的business-to-customer (B2C)邮件，包括账单、旅馆确认信、促销等等。这些邮件数量极多但基本是由固定的template生成的，Google想提取有用信息供自己的assisitive类产品使用，比如让Google Assistant能够回答账单什么时候要付之类的问题。

## Challenges and Basic Ideas
就像design principles总结的，设计难点是scalability/simplicity/safety。

k-anonymity

无论Juicer还是Crusher，都由三部分逻辑组成：
1. template induction
2. machine-learned rule generation
3. online extraction


## Juicer


### Template Induction
conflation/segmentation

## Crusher
一言以蔽之，Crusher的改进就是把template induction从offline挪到了online。

staged event-driven (SEDA)架构

**Why not stream processing framework？**


## Summary
