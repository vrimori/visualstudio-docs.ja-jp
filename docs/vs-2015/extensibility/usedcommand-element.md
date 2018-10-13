---
title: UsedCommand 要素 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: abcc3117b46cca424388b849f9baf26d79ca270e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49194643"
---
# <a name="usedcommand-element"></a>UsedCommand 要素
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

他の .vsct ファイルで定義されているコマンドにアクセスするために VSPackage を使用できます。 例では、VSPackage は、標準を使用している場合、**コピー**コマンドで定義されている、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]シェルは、コマンドを追加するメニューまたはツールバー再実装せずします。  
  
## <a name="syntax"></a>構文  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|guid|必須。 コマンドを識別する GUID ID のペアの GUID です。|  
|ID|必須。 コマンドを識別する GUID ID のペアの ID。|  
|条件|任意。 参照してください[条件付き属性](../extensibility/vsct-xml-schema-conditional-attributes.md)します。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|なし||  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[UsedCommands 要素](../extensibility/usedcommands-element.md)|UsedCommand 要素をグループ化し、他の UsedCommands グループ化します。|  
  
## <a name="remarks"></a>Remarks  
 コマンドを追加することによって、`<UsedCommands>`要素、VSPackage の通知、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]環境、VSPackage にコマンドが必要です。 追加する必要があります、`<UsedCommand>`パッケージが必要とする任意のコマンドの要素がすべてのバージョンと Visual Studio の構成に含まれません。 など、パッケージが Visual C に固有のコマンドを呼び出す場合のコマンドは、するには Visual Web Developer のユーザーが使用できる含める、`<UsedCommand>`コマンドの要素。  
  
## <a name="example"></a>例  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>関連項目  
 [UsedCommands 要素](../extensibility/usedcommands-element.md)   
 [Visual Studio Command Table (.Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

