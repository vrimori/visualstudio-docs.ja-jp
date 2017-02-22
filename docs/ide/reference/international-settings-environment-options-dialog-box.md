---
title: "[国際対応の設定] ([オプション] ダイアログ ボックス - [環境]) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Environment.InternationalSettings"
  - "VS.ToolsOptionsPages.Environment.International_Settings"
  - "VS.Environment.International Settings"
  - "VS.ToolsOptionsPag.Environment.International_Settings"
helpviewer_keywords: 
  - "[国際対応の設定] ダイアログ ボックス"
  - "言語、環境設定"
  - "[オプション] ダイアログ ボックス、国際対応の設定"
  - "言語、既定値の指定"
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# [国際対応の設定] ([オプション] ダイアログ ボックス - [環境])
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

コンピューターにインストールされている統合開発環境 \(IDE\) に複数の言語バージョンがある場合は、\[国際対応の設定\] ページで既定の言語を変更できます。  このダイアログ ボックスにアクセスするには、**\[ツール\]** メニューの **\[オプション\]** を選択し、**\[環境\]** フォルダーから **\[国際対応の設定\]** を選択します。  このページが一覧に表示されない場合は、**\[オプション\]** ダイアログ ボックスの **\[すべての設定を表示\]** を選択します。  
  
> [!NOTE]
>  使用している設定またはエディションによっては、ダイアログ ボックスで使用可能なオプションや、メニュー コマンドの名前や位置がヘルプに記載されている内容と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
 **言語**  
 インストールされている製品の言語バージョンで使用可能な言語の一覧が表示されます。  コンピューターに複数の言語バージョンがインストールされていない場合、このオプションは使用できません。  複数言語の製品または混合言語の製品で環境を共有する場合は、言語の選択が **\[Microsoft Windows と同じ\]** に変更されます。  
  
> [!CAUTION]
>  複数の言語がインストールされているシステムでは、Visual C\+\+ ビルド ツール \(cl.exe、link.exe、nmake.exe、bscmake.exe、および関連ファイル\) はこの設定による影響を受けません。  Visual C\+\+ ビルド ツールはサテライト DLL モデルを使用しないため、これらのツールは最後にインストールされた言語のバージョンを使用し、以前にインストールされた言語のツールは上書きされます。  
  
## 参照  
 [複数言語バージョンの Visual Studio のインストール](../Topic/Installing%20Multiple%20Language%20Versions%20of%20Visual%20Studio.md)   
 [\[環境\] \(\[オプション\] ダイアログ ボックス\)](../Topic/Environment%20Options%20Dialog%20Box.md)