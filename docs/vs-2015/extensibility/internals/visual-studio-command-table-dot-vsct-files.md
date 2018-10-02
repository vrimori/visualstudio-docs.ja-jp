---
title: Visual Studio コマンド テーブル (します。Vsct) ファイル |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0692f0b32544edf7d5d7cec4b0ab4592c4219b3a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47545987"
---
# <a name="visual-studio-command-table-vsct-files"></a>Visual Studio Command Table (.Vsct) ファイル
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Visual Studio Command Table (します。Vsct) ファイル](https://docs.microsoft.com/visualstudio/extensibility/internals/visual-studio-command-table-dot-vsct-files)します。  
  
コマンド テーブル構成ファイルは、VSPackage を含むコマンドのセットを説明するテキスト ファイルです。 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]コマンド テーブル (VSCT) コンパイラは、テーブルのバイナリ コマンドの出力 (.cto) ファイルに XML ベースの構成ファイル (.vsct ファイル) をコンパイルします。 結果の .cto ファイルは、.ctc 構成ファイルをコンパイルするコマンド テーブル (CTC) コンパイラを使用して作成されるものと同じです。 ただし、XML ベースの .vsct ファイルでは、XML エディターと XML IntelliSense などのいくつかの利点があります。  
  
 構文とセマンティクス .vsct ファイルの詳細については、次を参照してください。 [XML コマンド テーブルの設計 (します。Vsct) ファイル](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
  
## <a name="in-this-section"></a>このセクションの内容  
 [XML コマンド テーブル (.Vsct) ファイルの設計](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
 .Vsct ファイルを設計する方法について説明します。  
  
 [方法: .Vsct ファイルを作成する](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)  
 .Vsct ファイルを作成する方法を比較します。 新しい .vsct ファイルを手動で作成するためのプロセスについて説明します。  
  
## <a name="related-sections"></a>関連項目  
 [VSCT XML スキーマ リファレンス](../../extensibility/vsct-xml-schema-reference.md)  
 コマンド テーブルの XML 構成ファイルの各セクションについてを説明します。  
  
 [コマンド テーブルの構成 (します。Ctc) ファイル](http://msdn.microsoft.com/en-us/3413dda1-f372-4669-bcf0-c64d3463842c)  
 非推奨の .ctc ファイル形式の概要を示します。  
  
 [VSPackage でユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 コマンド テーブル形式の仕様について説明します。  
  
 [VSPackage のリソース](../../extensibility/internals/resources-in-vspackages.md)  
 マネージ Vspackage でマネージ コードとアンマネージ リソースを使用する方法について説明します。  
  
 [コマンド、メニュー、およびツール バー](../../extensibility/internals/commands-menus-and-toolbars.md)  
 メニュー、ツール バー、およびコマンド コンボ ボックスが含まれている UI を作成する方法について説明します。

