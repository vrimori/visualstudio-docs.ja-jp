---
title: 要素をシンボル |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 87e9159e1e392ff242407b105589f4f33341b45b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142777"
---
# <a name="symbols-element"></a>シンボル要素
Guid および他の VSCT 要素によって使用されている Id を定義します。 アンマネージ コードは、この情報、通常で指定されているヘッダー ファイルから[Extern 要素](../extensibility/extern-element.md)です。 マネージ コードが、要素の子要素、シンボルをこの情報を定義します。  
  
 既存の .cto ファイルから .vsct ファイルを作成する場合、シンボルがシンボル要素の子として生成されます。 詳細については、次を参照してください。[する方法: を作成します。既存の Vsct ファイルです。Cto ファイル](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file)です。  
  
 シンボル要素がないと混同しないでください、[定義要素](../extensibility/define-element.md)プリプロセッサで使用するための名前と値のペアを定義します。  
  
## <a name="syntax"></a>構文  
  
```  
<Symbols>  
  <GuidSymbol>... </GuidSymbol>  
  <GuidSymbol>... </GuidSymbol>  
</Symbols>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|なし||  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|GuidSymbol|GUID 記号を定義します。 GuidSymbol は 2 つの必須属性を持つ: 名前と値。 名前は、シンボルの名前と値は GUID を文字列としての値。<br /><br /> 例:\<GuidSymbol 名"guidVsPackage1Pkg"の値を = ="{c5f54698-101a-4846-84d3-dc748f9cd848}"/>|  
|IDSymbol|シンボルを定義します。 IDSymbol は 2 つの必須属性を持つ: 名前と値。 名前は、シンボルの名前と値が文字列としての記号の値。<br /><br /> 例:\<IDSymbol 名"MyMenuGroup"の値を = ="0x1020"/>|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[CommandTable 要素](../extensibility/commandtable-element.md)|.Vsct ファイルのルート要素です。|  
  
## <a name="example"></a>例  
  
```  
<Symbols>  
  <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />  
  <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}">  
    <IDSymbol name="MyMenuGroup" value="0x1020" />  
    <IDSymbol name="cmdidMyCommand" value="0x0100" />  
    <IDSymbol name="cmdidMyTool" value="0x0101" />  
  </GuidSymbol>  
</Symbols>  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio Command Table (.Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)