---
title: 要素の定義 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2596023628086ce5e921eeb8499956828d4c8a5c
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497162"
---
# <a name="define-element"></a>要素を定義します。
シンボルの名前と値のペアを定義します。 このシンボルは、条件付き属性によって評価されることができます。 詳細については、次を参照してください。[条件付き属性](../extensibility/vsct-xml-schema-conditional-attributes.md)します。 参照してください、 [Symbols 要素](../extensibility/symbols-element.md)します。  
  
## <a name="syntax"></a>構文  
  
```  
<Define name="Mode" value="Standard" />  
```  
  
## <a name="attributes-and-elements"></a>属性と要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|name|必須。 シンボルの名前。<br /><br /> 名前 =「モード」|  
|値|必須。 シンボルの値です。<br /><br /> 値 ="Standard"|  
|条件|任意。 詳細については、次を参照してください。[条件付き属性](../extensibility/vsct-xml-schema-conditional-attributes.md)します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[CommandTable 要素](../extensibility/commandtable-element.md)|統合開発環境 (IDE) には、VSPackage を提供するコマンドを表すすべての要素を定義します。 たとえば、メニュー項目、メニューのツールバー、およびコンボ ボックス。|  
  
## <a name="example"></a>例  
  
```  
<Define name="DEMO_UI"/>  
<Define name="MODE" value="Standard"/>  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio コマンド テーブル (.vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)