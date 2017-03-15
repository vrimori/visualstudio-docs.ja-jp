---
title: "VSCT XML スキーマ リファレンス | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio コマンド テーブル構成ファイル (VSCT)、XML スキーマ"
  - "VSCT XML スキーマ要素"
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# VSCT XML スキーマ リファレンス
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

コマンド テーブル コンパイラ スキーマの要素のテーブルの各要素と属性に、許可されている子で提供します。  
  
 XML ベースのコマンド テーブル構成 \(.vsct\) ファイルは、統合開発環境 \(IDE\) に VSPackage を提供するコマンドの要素を定義します。 これらの要素には、メニュー項目、メニューのツールバー、およびコンボ ボックスが含まれます。  
  
> [!NOTE]
>  VSCT コンパイラでは、.vsct ファイルに対してプリプロセッサを実行できます。 これは、通常、C プリプロセッサでは、定義することが含まれていて、マクロの C\+\+ ファイルで使用されているのと同じ構文します。 この例としては、.vsct で提供されるファイルを **新しいプロジェクト** ウィザード VSPackage プロジェクト用に作成します。  
  
## 省略可能な要素  
 一部の VSCT 要素は省略できます。 場合、 `Parent` 引数が指定されていない、Group\_Undefined:0 を暗黙的に指定されます。 場合、 `Icon` 引数が指定されていない、guidOfficeIcon:msotcidNoIcon を暗黙的に指定されます。 ショートカット キーが定義されている場合、通常使用されていないのエミュレーションはオプションです。  
  
 ビットマップ ストリップの場所を指定してコンパイル時にビットマップの項目を埋め込むことがあります、 `href` 引数。 ビットマップ ストリップを DLL のリソースから抽出されたなくにマージ中にコピーされます。 ときに、 `href` 引数が指定されて、 `usedList` 引数が省略可能なそのビットマップ ストリップ内のすべてのスロットでは、使用されると見なされます。  
  
 すべての GUID と ID の値は、シンボル名を使用して定義する必要があります。 これらの名前は、ヘッダー ファイルまたは VSCT \< シンボル \> セクションに定義できます。 シンボル名は、\< Include \> 要素を含めるか、\< Extern \> 要素によって参照される、ローカル、する必要があります。 シンボリック名が、パターンに従う場合、単純なは、\< Extern \> 要素で指定されたヘッダー ファイルからインポートされた \#define シンボル値です。 値は、そのシンボルが以前に定義されていれば、別のシンボルにすることがあります。 GUID の定義は、OLE または C\+\+ のいずれかの形式に準拠する必要があります。 ID の値は、次の行に示すように 10 進または 16 進数、0 x は、前のいずれかにもなる場合があります。  
  
-   {6D484634\-E53D\-4a2c\-ADCB\-55145C9362C8}  
  
-   {0x6d484634、0xe53d、0x4a2c、{0xad、0xcb、0x55、0x14、0x5c、0x93、0x62、0xc8}}  
  
 XML コメントを使用することがありますは、ラウンドト リップのグラフィカル ユーザー インターフェイス \(GUI\) ツールが破棄可能性があります。 \< Annotation \> 要素の内容を形式に関係なく保持することが保証されます。  
  
## スキーマの階層  
 .Vsct ファイルには、次の主要な要素があります。  
  
 [CommandTable 要素](../extensibility/commandtable-element.md)  
  
 [Extern 要素](../extensibility/extern-element.md)  
  
 [要素が含まれます](../extensibility/include-element.md)  
  
 [要素を定義します。](../extensibility/define-element.md)  
  
 [Commands 要素](../extensibility/commands-element.md)  
  
 [CommandPlacements 要素](../extensibility/commandplacements-element.md)  
  
 [VisibilityConstraints 要素](../extensibility/visibilityconstraints-element.md)  
  
 [ショートカット キーの要素](../extensibility/keybindings-element.md)  
  
 [UsedCommands 要素](../extensibility/usedcommands-element.md)  
  
 [Parent 要素](../extensibility/parent-element.md)  
  
 [Icon 要素](../extensibility/icon-element.md)  
  
 [文字列の要素](../extensibility/strings-element.md)  
  
 [コマンドのフラグ要素](../extensibility/command-flag-element.md)  
  
 [シンボル要素](../extensibility/symbols-element.md)  
  
 [条件付きの属性](../extensibility/vsct-xml-schema-conditional-attributes.md)  
  
## 参照  
 [Vspackage でのユーザー インターフェイス要素を追加する方法](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Vspackage でルーティング コマンド](../extensibility/internals/command-routing-in-vspackages.md)