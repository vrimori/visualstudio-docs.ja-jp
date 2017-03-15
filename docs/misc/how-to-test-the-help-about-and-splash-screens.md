---
title: "方法: バージョン情報とスプラッシュ スクリーンをテストする | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[バージョン情報] ダイアログ ボックス"
  - "VSPackage、スプラッシュ スクリーン"
  - "VSPackage、ブランド化"
ms.assetid: 2b959fa4-56d3-44f4-8c2d-9ea2e6fb269d
caps.latest.revision: 10
caps.handback.revision: 10
manager: "douge"
---
# 方法: バージョン情報とスプラッシュ スクリーンをテストする
**\*\*\* Help About \*\*\***スプラッシュ スクリーンのサポートを実行した後[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の実装をテストできます。  
  
### ダイアログ ボックスに関するヘルプをテストするには  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のコマンド プロンプトで**\/setup** スイッチを指定して devenv.exe を実行します。  実験環境で実行するには検証する :  
  
     **devenv \/rootsuffix Exp \/setup**  
  
     **\*\*\* Help About \*\*\*** 画面の情報を変更したときのみ **メモ**  この手順を繰り返す必要があります。  
  
2.  前述した **\/setup**スイッチなしで実行します。[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を同じレジストリのルート :  
  
     **devenv \/rootsuffix Exp**  
  
3.  \[ENT0ENT\] メニューの \[ENT1ENT\] をクリックします。  
  
     VSPackage の名前は \[入力\] ENT0ENT リストに表示されます。  
  
4.  VSPackage の一覧からを選択します。  
  
     VSPackage の製品情報は ENT0ENT \[入力\] ボックスに表示されます。  
  
### スプラッシュ スクリーンをテストするには  
  
1.  **\/setup** スイッチを指定して devenv.exe を実行します。  実験環境で実行するには検証する :  
  
     **devenv \/rootsuffix Exp \/setup**  
  
     スプラッシュ スクリーンの情報を変更したときのみ **メモ**  この手順を繰り返す必要があります。  
  
2.  前述した **\/splash**スイッチを実行すると **\/setup** スイッチではなくとを同じ [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のレジストリ ルートの。  
  
     **devenv \/rootsuffix Exp \/splash**  
  
     VSPackage の製品情報とロゴはスプラッシュ スクリーンに表示されます。  
  
## 参照  
 [VSPackage のブランド化](/visual-cpp/misc/vspackage-branding)