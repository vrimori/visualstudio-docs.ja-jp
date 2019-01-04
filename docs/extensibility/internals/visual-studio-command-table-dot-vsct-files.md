---
title: Visual Studio コマンド テーブル (します。Vsct) ファイル |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 05c154a7ba87101f4a747b58d1a9ae4de16b7062
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53988872"
---
# <a name="visual-studio-command-table-vsct-files"></a>Visual Studio Command Table (.Vsct) ファイル
コマンド テーブル構成ファイルは、VSPackage を含むコマンドのセットを説明するテキスト ファイルです。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]コマンド テーブル (VSCT) コンパイラは、テーブルのバイナリ コマンドの出力 (.cto) ファイルに XML ベースの構成ファイル (.vsct ファイル) をコンパイルします。 結果の .cto ファイルは、.ctc 構成ファイルをコンパイルするコマンド テーブル (CTC) コンパイラを使用して作成されるものと同じです。 ただし、XML ベースの .vsct ファイルでは、XML エディターと XML IntelliSense などのいくつかの利点があります。  
  
 構文とセマンティクス .vsct ファイルの詳細については、次を参照してください。 [XML コマンド テーブルの設計 (します。Vsct) ファイル](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
  
## <a name="in-this-section"></a>このセクションの内容  
 [XML コマンド テーブル (.Vsct) ファイルの設計](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
 .Vsct ファイルを設計する方法について説明します。  
  
 [方法: 作成します。Vsct ファイル](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)  
 .Vsct ファイルを作成する方法を比較します。 新しい .vsct ファイルを手動で作成するためのプロセスについて説明します。  
  
## <a name="related-sections"></a>関連項目  
 [VSCT XML スキーマ リファレンス](../../extensibility/vsct-xml-schema-reference.md)  
 コマンド テーブルの XML 構成ファイルの各セクションについてを説明します。  
  
 [コマンド テーブルの構成 (します。Ctc) ファイル](https://msdn.microsoft.com/library/3413dda1-f372-4669-bcf0-c64d3463842c)  
 非推奨の .ctc ファイル形式の概要を示します。  
  
 [VSPackage でユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 コマンド テーブル形式の仕様について説明します。  
  
 [VSPackage のリソース](../../extensibility/internals/resources-in-vspackages.md)  
 マネージ Vspackage でマネージ コードとアンマネージ リソースを使用する方法について説明します。  
  
 [コマンド、メニュー、およびツール バー](../../extensibility/internals/commands-menus-and-toolbars.md)  
 メニュー、ツール バー、およびコマンド コンボ ボックスが含まれている UI を作成する方法について説明します。