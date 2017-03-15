---
title: "/Out (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/out DEVENV スイッチ"
  - "ビルド [Visual Studio], エラー"
  - "ビルド [Visual Studio], ログ"
  - "Devenv, /out スイッチ"
  - "エラー ログ [Visual Studio]"
  - "エラー ログ [Visual Studio], コマンド ラインでのビルド エラー"
  - "エラー [Visual Studio], ビルド"
  - "out DEVENV スイッチ"
  - "出力ファイル, ビルド エラー"
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Out (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ソリューションを実行、ビルド、リビルド、または配置したときに、エラーを格納し表示するファイルを指定します。  
  
## 構文  
  
```  
devenv /out FileName  
```  
  
## 引数  
 `FileName`  
 必ず指定します。  実行可能ファイルのビルド時にエラーを受け取るファイルのパスと名前です。  
  
## 解説  
 指定したファイル名が存在しない場合は、自動的に作成されます。  ファイルが既に存在する場合、結果はファイルの既存の内容に追加されます。  
  
 コマンド ラインのビルド エラーは、**\[コマンド\]** ウィンドウと **\[出力\]** ウィンドウの \[ソリューション ビルダー\] ビューに表示されます。  このオプションは、無人操作でビルドを実行して結果を表示する必要がある場合に便利です。  
  
## 使用例  
 `MySolution` を実行し、エラーをファイル `MyErrorLog.txt` に書き込むコードは次のとおりです。  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"  
```  
  
## 参照  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)   
 [\/Run](../../ide/reference/run-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Deploy](../../ide/reference/deploy-devenv-exe.md)