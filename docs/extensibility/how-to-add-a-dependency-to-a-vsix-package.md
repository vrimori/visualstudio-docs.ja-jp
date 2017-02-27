---
title: "方法: VSIX パッケージへの依存関係の追加 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "パッケージのリファレンス"
  - "パッケージのアセンブリ"
  - "dll をパッケージ化します。"
  - "vsix の参照"
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 方法: VSIX パッケージへの依存関係の追加
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ターゲット コンピューターに含まれていない任意の依存関係をインストールする VSIX パッケージの配置を設定することができます。 これを実現するには、VSIX の依存関係 source.extension.vsixmanifest ファイルにはが含まれます。  
  
#### 依存関係を追加するには  
  
1.  Source.extension.vsixmanifest ファイルを開き、 **デザイン** 表示します。 移動して、 **の依存関係** \] タブでをクリックし、 **新規**します。  
  
2.  インストールされている拡張子を追加する: で、 **新しい依存関係の追加** ダイアログ ボックスで、 **拡張機能をインストール** およびその後、 **名**, 、一覧上の拡張機能を選択します。  
  
3.  インストールされていない別の VSIX に追加する:: で、 **新しい依存関係の追加** ダイアログ ボックスで、 **ファイル システム上のファイル** し、使用して、 **参照** VSIX を選択する\] ボタンをクリックします。  
  
## 参照  
 [VSIX 拡張機能スキーマ 1.0 リファレンス](http://msdn.microsoft.com/ja-jp/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [VSIX パッケージの構造](../extensibility/anatomy-of-a-vsix-package.md)   
 [Windows インストーラーの配置の拡張機能を準備します。](../extensibility/preparing-extensions-for-windows-installer-deployment.md)