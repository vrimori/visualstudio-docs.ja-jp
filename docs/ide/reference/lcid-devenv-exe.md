---
title: "/LCID (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/l DEVENV スイッチ"
  - "/lcid Devenv スイッチ"
  - "Devenv, /LCID スイッチ"
  - "言語 (既定の)"
  - "LCID devenv スイッチ"
  - "ロケール ID"
  - "ロケール ID, 設定 (IDE に対する)"
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /LCID (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

統合開発環境 \(IDE: Integrated Development Environment\) 内の文字列、通貨、およびその他の値に使用する既定の言語を設定します。  
  
## 構文  
  
```  
devenv {/LCID|/l} LocaleID  
```  
  
## 引数  
 `LocaleID`  
 必ず指定します。  指定の言語のロケール ID \(LCID: Locale ID\) です。  
  
## 解説  
 IDE を読み込み、環境で使用する既定の言語を設定します。  変更内容は複数のセッションを通じて保持され、IDE の **\[オプション\]** ダイアログ ボックスの **\[環境\]** にある **\[国際対応の設定\]** ペインに反映されます。  
  
 指定した言語がユーザーのシステムで使用できない場合、\/LCID スイッチは無視されます。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] でサポートされる言語の LCID の一覧を次の表に示します。  
  
|言語|LCID|  
|--------|----------|  
|簡体字中国語|2052|  
|繁体字中国語|1028|  
|英語|1033|  
|フランス語|1036|  
|ドイツ語|1031|  
|イタリア語|1040|  
|日本語|1041|  
|韓国語|1042|  
|スペイン語|3082|  
  
## 使用例  
 英語のリソース文字列を使用して IDE を読み込むコードは次のとおりです。  
  
```  
devenv /LCID 1033  
```  
  
## 参照  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)   
 [\[国際対応の設定\] \(\[オプション\] ダイアログ ボックス \- \[環境\]\)](../Topic/International%20Settings,%20Environment,%20Options%20Dialog%20Box.md)   
 [ウィンドウ レイアウトをカスタマイズする](../../ide/customizing-window-layouts-in-visual-studio.md)