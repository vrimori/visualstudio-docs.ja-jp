---
title: "方法 : ClickOnce アプリケーションにデータ ファイルを含める | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce 配置, データ"
  - "データ アクセス, ClickOnce アプリケーション"
  - "配置 (アプリケーションを) [ClickOnce], データ ファイル"
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法 : ClickOnce アプリケーションにデータ ファイルを含める
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

インストールする各 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションには、そのアプリケーションの独自のデータを管理するためのディレクトリが、インストール先コンピューターのローカル ディスクに作成されます。  テキスト ファイルや XML ファイルだけでなく、Microsoft Access データベース \(.mdb\) ファイルなど任意の種類のファイルをデータ ファイルとして扱うことができます。  任意の種類のデータ ファイルを [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションに追加するための手順を次に示します。  
  
### Mage.exe を使用してデータ ファイルをアプリケーションに含めるには  
  
1.  アプリケーションの他のファイルと共にデータ ファイルをアプリケーション ディレクトリに格納します。  
  
     一般に、このアプリケーション ディレクトリは、v1.0.0.0 などの配置の現在のバージョン名が付けられたディレクトリです。  
  
2.  データ ファイルを一覧に含めるために、アプリケーション マニフェストを更新します。  
  
     **mage \-u v1.0.0.0\\Application.manifest \-FromDirectory v1.0.0.0**  
  
     このタスクを実行すると、アプリケーション マニフェストのファイル一覧が再作成され、ハッシュ署名が自動生成されます。  
  
3.  任意のテキスト エディターまたは XML エディターで、アプリケーション マニフェストを開き、先ほど追加したファイルの `file` 要素を探します。  
  
     `Data.xml` という XML ファイルを追加している場合は、次のコード例のようなファイルになります。  
  
 `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  この要素に `type` 属性を追加し、この属性の値に `data` を設定します。  
  
 `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  キー ペアまたは証明書を使用してアプリケーション マニフェストに再署名し、次に配置マニフェストに再署名します。  
  
     配置マニフェストは、アプリケーション マニフェストのハッシュが変更されているため、再署名する必要があります。  
  
     **mage \-s app manifest \-cf cert\_file \-pwd password**  
  
     **mage \-u deployment manifest \-appm app manifest**  
  
     **mage \-s deployment manifest \-cf certfile \-pwd password**  
  
### MageUI.exe を使用してデータ ファイルをアプリケーションに含めるには  
  
1.  アプリケーションの他のファイルと共にデータ ファイルをアプリケーション ディレクトリに格納します。  
  
2.  一般に、このアプリケーション ディレクトリは、v1.0.0.0 などの配置の現在のバージョン名が付けられたディレクトリです。  
  
3.  **\[File\]** メニューの **\[Open\]** をクリックし、アプリケーション マニフェストを開きます。  
  
4.  **\[Files\]** タブをクリックします。  
  
5.  ページの先頭にあるボックスに、アプリケーションのファイルが格納してあるディレクトリを入力し、**\[Populate\]** をクリックします。  
  
     データ ファイルがグリッドに表示されます。  
  
6.  データ ファイルの **\[File Type\]** 値を **\[データ\]** に設定します。  
  
7.  アプリケーション マニフェストを保存してからファイルに再署名します。  
  
     MageUI.exe から、ファイルに署名し直すように求めるメッセージが表示されます。  
  
8.  配置マニフェストに再署名します。  
  
     配置マニフェストは、アプリケーション マニフェストのハッシュが変更されているため、再署名する必要があります。  
  
## 参照  
 [ClickOnce アプリケーションにおけるローカル データおよびリモート データへのアクセス](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)