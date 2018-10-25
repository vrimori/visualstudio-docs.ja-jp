---
title: UsedCommand 要素 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4f7df36c05de0d8dc2f68ab8e41afa11366276b9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49856302"
---
# <a name="usedcommand-element"></a>UsedCommand 要素
他の .vsct ファイルで定義されているコマンドにアクセスするために VSPackage を使用できます。 例では、VSPackage は、標準を使用している場合、**コピー**コマンドで定義されている、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]シェルは、コマンドを追加するメニューまたはツールバー再実装せずします。  
  
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
 コマンドを追加することによって、`<UsedCommands>`要素、VSPackage の通知、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]環境、VSPackage にコマンドが必要です。 追加する必要があります、`<UsedCommand>`パッケージが必要とする任意のコマンドの要素がすべてのバージョンと Visual Studio の構成に含まれません。 など、パッケージが Visual C に固有のコマンドを呼び出す場合のコマンドは、するには Visual Web Developer のユーザーが使用できる含める、`<UsedCommand>`コマンドの要素。  
  
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