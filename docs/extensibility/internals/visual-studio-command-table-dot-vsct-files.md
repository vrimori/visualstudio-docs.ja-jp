---
title: "Visual Studio コマンド テーブル (です。Vsct) ファイル |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ace754b9d6ddb220b3647b281011d3763810987c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="visual-studio-command-table-vsct-files"></a>Visual Studio コマンド テーブル (です。Vsct) ファイル
コマンド テーブルの構成ファイルは、VSPackage を含むコマンドのセットを説明するテキスト ファイルです。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]コマンド テーブル (VSCT) コンパイラが XML ベースの構成ファイル (.vsct ファイル) をテーブルのバイナリ コマンドの出力 (.cto) ファイルにコンパイルします。 結果の .cto ファイル、.ctc 構成ファイルをコンパイルするコマンド テーブル (CTC) コンパイラを使用して作成されたものと同じです。 ただし、XML ベースの .vsct ファイルでは、XML エディターや XML IntelliSense などのいくつかの利点があります。  
  
 .Vsct ファイルのセマンティクスと構文に関する詳細についてを参照してください。 [XML コマンド テーブルのデザイン (です。Vsct) ファイル](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
  
## <a name="in-this-section"></a>このセクションの内容  
 [XML コマンド テーブル (.Vsct) ファイルの設計](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
 .Vsct ファイルをデザインする方法について説明します。  
  
 [方法: .Vsct ファイルを作成する](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)  
 .Vsct ファイルを作成するためのメソッドを比較します。 新しい .vsct ファイルを手動で作成するプロセスについて説明します。  
  
## <a name="related-sections"></a>関連項目  
 [VSCT XML スキーマ リファレンス](../../extensibility/vsct-xml-schema-reference.md)  
 コマンド テーブルの XML 構成ファイルの各セクションで詳しくを説明します。  
  
 [コマンド テーブルの構成 (です。Ctc) ファイル](http://msdn.microsoft.com/en-us/3413dda1-f372-4669-bcf0-c64d3463842c)  
 非推奨の .ctc ファイル形式の概要を示します。  
  
 [VSPackage でユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 コマンド テーブル形式の指定について説明します。  
  
 [VSPackage のリソース](../../extensibility/internals/resources-in-vspackages.md)  
 マネージ Vspackage でマネージ リソースとアンマネージ リソースを使用する方法について説明します。  
  
 [コマンド、メニュー、およびツール バー](../../extensibility/internals/commands-menus-and-toolbars.md)  
 メニュー、ツール バー、およびコマンド コンボ ボックスが含まれている UI を作成する方法について説明します。