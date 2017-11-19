---
title: "方法: VSIX パッケージへの依存関係の追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d3f3b54e19d8418f35a733b73ea0616b53bd42ce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>方法: VSIX パッケージへの依存関係の追加
ターゲット コンピューターに含まれていないすべての依存関係をインストールする VSIX パッケージの配置を設定することができます。 これを実現するには、source.extension.vsixmanifest ファイルを VSIX の依存関係が含まれます。  
  
#### <a name="to-add-a-dependency"></a>依存関係を追加するには  
  
1.  Source.extension.vsixmanifest ファイルを開き、**デザイン**ビュー。 移動して、**の依存関係** タブでをクリックし、**新規**です。  
  
2.  インストールした拡張機能を追加する: で、**新しい依存関係の追加**ダイアログ ボックスで、**拡張機能がインストールされている**し、**名前**一覧に拡張機能を選択します。  
  
3.  インストールされていない別の VSIX に追加する:: で、**新しい依存関係の追加**ダイアログ ボックスで、**ファイル システム上のファイル**しを使用して、**参照**VSIX を選択するボタンをクリックします。  
  
## <a name="see-also"></a>関連項目  
 [VSIX 拡張機能スキーマ 1.0 リファレンス](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [VSIX パッケージの構造](../extensibility/anatomy-of-a-vsix-package.md)   
 [Windows インストーラーの配置に関する拡張機能を準備する](../extensibility/preparing-extensions-for-windows-installer-deployment.md)