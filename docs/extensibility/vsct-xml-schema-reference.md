---
title: VSCT XML スキーマ リファレンス |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 51be3e86f1f19cc3701dd456b3085d3e8993b7a8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915556"
---
# <a name="vsct-xml-schema-reference"></a>VSCT XML スキーマ リファレンス
コマンド テーブル コンパイラ スキーマの要素のテーブルの各要素と属性に、許可されている子を提供します。  
  
 XML ベースのコマンド テーブル (.vsct) の構成ファイルでは、統合開発環境 (IDE) に VSPackage を提供するコマンド要素を定義します。 これらの要素には、メニュー項目、メニューのツールバー、およびコンボ ボックスが含まれます。  
  
> [!NOTE]
>  VSCT コンパイラでは、.vsct ファイルでプリプロセッサを実行できます。 これは通常は、C プリプロセッサを定義することに含まれる C++ ファイルで使用されているのと同じ構文をあるマクロ、します。 これの例を示しますが、.vsct で提供されているファイルを**新しいプロジェクト**ウィザードは、VSPackage プロジェクトを作成します。  
  
## <a name="optional-elements"></a>省略可能な要素  
 一部の VSCT 要素は省略可能です。 場合、`Parent`引数が指定されていない、Group_Undefined:0 を暗黙的に指定されます。 場合、`Icon`引数が指定されていない、guidOfficeIcon:msotcidNoIcon を暗黙的に指定されます。 ショートカット キーが定義されている場合は、エミュレーションでは、通常使用されていないは省略可能です。  
  
 ビットマップ ストリップの場所を指定して、コンパイル時にビットマップの項目を埋め込むことができます、`href`引数。 ビットマップ ストリップを DLL のリソースから抽出されたなくにマージ中にコピーされます。 ときに、`href`引数が指定されて、`usedList`引数が省略可能、およびビットマップ ストリップ内のすべてのスロットが使用されると見なされます。  
  
 すべての GUID と ID の値は、シンボリック名を使用して定義する必要があります。 VSCT でまたはヘッダー ファイルでは、これらの名前を定義することがあります\<シンボル > セクション。 シンボル名は、する必要があります、ローカルに格納\<Include > 要素、またはによって参照される\<Extern > 要素。 シンボリック名がで指定されたヘッダー ファイルからインポートされた、 \<Extern > 要素の単純なパターンに従っている場合は #define シンボル値です。 値は、そのシンボルが以前に定義されていれば、別のシンボルにすることがあります。 GUID の定義は、OLE または C++ のいずれかの形式に従う必要があります。 ID 値がありますの 10 進または 16 進数値 0 x は、前に、次の行で示すように。  
  
- {6D484634-E53D-4a2c-ADCB-55145C9362C8}  
  
- {0x6d484634、0xe53d、0x4a2c、{0xad、0xcb、0x55、0x14、0x5c、0x93、数 0x62、0xc8}}  
  
  XML コメントを使用する可能性がありますが、ラウンド トリップのグラフィカル ユーザー インターフェイス (GUI) ツールが破棄可能性があります。 内容\<注釈 > 要素の形式に関係なく保持することが保証されます。  
  
## <a name="schema-hierarchy"></a>スキーマの階層  
 .Vsct ファイルでは、次の主要な要素があります。  
  
 [CommandTable 要素](../extensibility/commandtable-element.md)  
  
 [Extern 要素](../extensibility/extern-element.md)  
  
 [要素を含める](../extensibility/include-element.md)  
  
 [要素を定義します。](../extensibility/define-element.md)  
  
 [Commands 要素](../extensibility/commands-element.md)  
  
 [CommandPlacements 要素](../extensibility/commandplacements-element.md)  
  
 [VisibilityConstraints 要素](../extensibility/visibilityconstraints-element.md)  
  
 [KeyBindings 要素](../extensibility/keybindings-element.md)  
  
 [UsedCommands 要素](../extensibility/usedcommands-element.md)  
  
 [親要素](../extensibility/parent-element.md)  
  
 [Icon 要素](../extensibility/icon-element.md)  
  
 [文字列の要素](../extensibility/strings-element.md)  
  
 [Command Flag 要素](../extensibility/command-flag-element.md)  
  
 [Symbols 要素](../extensibility/symbols-element.md)  
  
 [条件付き属性](../extensibility/vsct-xml-schema-conditional-attributes.md)  
  
## <a name="see-also"></a>関連項目  
 [Vspackage がユーザー インターフェイス要素を追加する方法](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Vspackage のコマンド ルーティング](../extensibility/internals/command-routing-in-vspackages.md)