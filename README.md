# PDF 压缩工具

一个基于 PDFTron（Apryse）PDFNet 的简单命令行工具，用于压缩（优化）PDF 文件，并输出压缩前后大小与压缩比。

## 功能特点
- 使用 PDFNet Optimizer 对 PDF 进行体积优化
- 线性化保存，提升网页快速预览体验
- 打印压缩前后大小与压缩比
- 简洁命令行使用方式

## 依赖与环境

必需依赖（第三方）：
- PDFNetPython3（PDFTron/Apryse 的 Python SDK 绑定）
- 安装：pip install PDFNetPython3

标准库（无需安装）：
- os
- sys

已在 Python 3 环境下开发与测试。

## 安装

1) 克隆仓库
- git clone https://github.com/yourname/yourrepo.git
- cd yourrepo

2) 安装依赖
- pip install PDFNetPython3

3) 配置 License（可选但建议）
- 在代码中找到 PDFNet.Initialize("demo:...") 并替换为你自己的 License Key。

## 使用方法

基本用法：
- python compress_pdf.py input.pdf output.pdf

参数说明：
- input.pdf：需要压缩的 PDF 文件路径
- output.pdf：压缩后输出的 PDF 文件路径

运行后，终端会打印类似如下的摘要信息：
- ## Summary ########################################################
- Input File:input.pdf
- Initial Size:12.34MB
- Output File:output.pdf
- Compressed Size:8.90MB
- Compression Ratio:27.89%.
- ###################################################################

## 代码结构

- compress_pdf.py
- get_size_format：字节大小转人类可读格式（KB/MB/GB…）
- compress_file：执行压缩（初始化 PDFNet、加载文档、Optimizer.Optimize、线性化保存、打印摘要）
- __main__：解析命令行参数并调用 compress_file

## 注意事项

- Demo License 限制：示例中的 demo key 仅用于演示，请更换为你自己的 License Key。
- 覆盖写入风险：如果你修改代码使 output_file 为空字符串，将会覆盖原文件。请谨慎操作。
- 加密 PDF：若 PDF 加密，需具备读取权限；代码已调用 doc.InitSecurityHandler()。
- 平台兼容：PDFNetPython3 提供多平台包，请确保与你的系统和 Python 版本匹配。

## 进一步改进（可选）

- 暴露可调压缩参数（图像质量、DPI、字体子集化等）
- 更健壮的命令行参数校验与帮助信息
- 默认输出文件名规则（例如 input.compressed.pdf），避免误覆盖
- 增加批量处理能力与日志输出