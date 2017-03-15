---
title: "Visual Studio コマンド テーブル (します。Vsct) ファイル | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT ファイル, 概要"
  - "Visual Studio コマンド テーブル構成ファイル (VSCT), 概要"
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
---
# Visual Studio コマンド テーブル (します。Vsct) ファイル
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

コマンド テーブル構成ファイルは、VSPackage を含むコマンドのセットを表すテキスト ファイルです。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] コマンド テーブル \(VSCT\) コンパイラが XML ベースの構成ファイル \(.vsct ファイル\) をテーブルのバイナリのコマンドの出力 \(.cto\) ファイルにコンパイルします。 結果の .cto ファイルは、.ctc 構成ファイルをコンパイルするコマンドのテーブル \(CTC\) コンパイラを使用して作成したものと同じです。 ただし、XML ベースの .vsct ファイルには、XML エディターや XML IntelliSense などのいくつかの利点があります。  
  
 .Vsct ファイルのセマンティクスと構文の詳細については、次を参照してください。 [XML コマンド テーブルの設計 \(します。Vsct\) ファイル](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
  
## このセクションの内容  
 [XML コマンド テーブルの設計 \(します。Vsct\) ファイル](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
 .Vsct ファイルをデザインする方法について説明します。  
  
 [方法: 作成します。Vsct ファイル](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)  
 .Vsct ファイルを作成するためのメソッドを比較します。 新しい .vsct ファイルを手動で作成するプロセスについて説明します。  
  
## 関連項目  
 [VSCT XML スキーマ リファレンス](../../extensibility/vsct-xml-schema-reference.md)  
 コマンド テーブルの XML 構成ファイルの各セクションで詳しくを説明します。  
  
 [Command Table Configuration \(.Ctc\) Files](http://msdn.microsoft.com/ja-jp/3413dda1-f372-4669-bcf0-c64d3463842c)  
 非推奨の .ctc ファイル形式の概要を示します。  
  
 [Vspackage でのユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 コマンド テーブルの形式の指定について説明します。  
  
 [Vspackage でのリソース](../../extensibility/internals/resources-in-vspackages.md)  
 マネージ VSPackages でマネージ リソースとアンマネージ リソースを使用する方法について説明します。  
  
 [コマンド、メニューのおよびツールバー](../../extensibility/internals/commands-menus-and-toolbars.md)  
 メニューのツールバー、およびコンボ ボックスにコマンドを含む UI を作成する方法について説明します。