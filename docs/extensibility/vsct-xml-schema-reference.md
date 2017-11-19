---
title: "VSCT XML スキーマ リファレンス |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1fc82041f8ab2790c63c271f85d573a3105ab8b0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="vsct-xml-schema-reference"></a>VSCT XML スキーマ リファレンス
コマンド テーブル コンパイラ スキーマの要素のテーブルの各要素と属性に、許可されている子と共に提供します。  
  
 XML ベースのコマンド テーブル (.vsct) の構成ファイルは、統合開発環境 (IDE) に VSPackage を提供するコマンド要素を定義します。 これらの要素には、メニュー項目、メニューのツールバー、およびコンボ ボックスが含まれます。  
  
> [!NOTE]
>  VSCT コンパイラは、.vsct ファイルに対してプリプロセッサを実行できます。 これは、通常ため C プリプロセッサを定義することが含まれていて、マクロの C++ ファイルで使用されているのと同じ構文します。 この例は、.vsct で説明するファイル、**新しいプロジェクト**ウィザード、VSPackage プロジェクト用に作成します。  
  
## <a name="optional-elements"></a>省略可能な要素  
 一部の VSCT 要素は省略できます。 場合、`Parent`引数が指定されていない、Group_Undefined:0 を暗黙的に指定されます。 場合、`Icon`引数が指定されていない、guidOfficeIcon:msotcidNoIcon を暗黙的に指定されます。 ショートカット キーが定義されている場合は、エミュレーションでは、通常使用されていないはオプションです。  
  
 ビットマップ項目は、ビットマップ ストリップ内の場所を指定してコンパイル時に埋め込みが、`href`引数。 ビットマップ ストリップがマージ中にコピーではなく、DLL のリソースから抽出します。 ときに、`href`引数が指定されて、`usedList`引数、省略可能になり、ビットマップ ストリップ内のすべてのスロットでは、使用すると見なされます。  
  
 シンボリック名を使用してすべての GUID と ID 値を定義する必要があります。 VSCT でまたはヘッダー ファイルでは、これらの名前を定義することがあります\<シンボル > セクションでします。 シンボル名は、する必要があります、ローカルに格納\<Include > 要素、またはによって参照される\<Extern > 要素。 シンボリック名がで指定されたヘッダー ファイルからインポートされた、 \<Extern > 要素の単純なパターンに従うこと場合 #define シンボル値です。 値は、そのシンボルが既に定義されている限り、別のシンボルにすることがあります。 GUID の定義は、OLE または C++ のいずれかの形式に従う必要があります。 ID の値は、次の行に示すように 10 進または 16 進数 0 x、末尾に挿入されるのいずれかにもなる場合があります。  
  
-   {6D484634-E53D-4a2c-ADCB-55145C9362C8}  
  
-   {0x6d484634、0xe53d、0x4a2c、{0xad、0xcb、0x55、0x14、0x5c、0x93、0x62、0xc8}}  
  
 XML コメントを使用することがありますは、ラウンド トリップのグラフィカル ユーザー インターフェイス (GUI) ツールが破棄可能性があります。 内容\<注釈 > 要素を書式設定に関係なく維持することが保証されます。  
  
## <a name="schema-hierarchy"></a>スキーマの階層  
 .Vsct ファイルでは、次の主要な要素があります。  
  
 [CommandTable 要素](../extensibility/commandtable-element.md)  
  
 [Extern 要素](../extensibility/extern-element.md)  
  
 [Include 要素](../extensibility/include-element.md)  
  
 [Define 要素](../extensibility/define-element.md)  
  
 [Commands 要素](../extensibility/commands-element.md)  
  
 [CommandPlacements 要素](../extensibility/commandplacements-element.md)  
  
 [VisibilityConstraints 要素](../extensibility/visibilityconstraints-element.md)  
  
 [KeyBindings 要素](../extensibility/keybindings-element.md)  
  
 [UsedCommands 要素](../extensibility/usedcommands-element.md)  
  
 [Parent 要素](../extensibility/parent-element.md)  
  
 [Icon 要素](../extensibility/icon-element.md)  
  
 [ 要素](../extensibility/strings-element.md)  
  
 [Command Flag 要素](../extensibility/command-flag-element.md)  
  
 [Symbols 要素](../extensibility/symbols-element.md)  
  
 [条件付き属性](../extensibility/vsct-xml-schema-conditional-attributes.md)  
  
## <a name="see-also"></a>関連項目  
 [Vspackage がユーザー インターフェイス要素を追加する方法](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Vspackage のコマンド ルーティング](../extensibility/internals/command-routing-in-vspackages.md)