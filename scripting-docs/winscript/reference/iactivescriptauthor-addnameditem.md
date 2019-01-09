---
title: IActiveScriptAuthor::AddNamedItem |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddNamedItem
ms.assetid: 951003b6-1c4a-4086-b7ce-2f128e007280
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 85c434ea17d41fb98300289c3161349f9d9f5a2f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094862"
---
# <a name="iactivescriptauthoraddnameditem"></a>IActiveScriptAuthor::AddNamedItem
スクリプト エンジンの名前空間を作成するには、ルート レベルの項目の名前を追加します。 A*ルート レベルの項目*オブジェクト、プロパティとメソッドを含めることができ、イベント ソースを含むことができます。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT AddNamedItem(  
   LPCOLESTR          pszName,  
   DWORD              dwFlags,  
   IDispatch          *pdisp  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszName`  
 [in]スクリプトの表示の項目の名前。 名前は、一意であり、永続化である必要があります。  
  
 `dwFlags`  
 [in]名前付きの項目に関連付けられているフラグです。 次の値の組み合わせになります。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|SCRIPTITEM_ISVISIBLE|0x00000002|項目の名前が、スクリプトの名前空間で使用できることを示します。 これにより、項目のプロパティ、メソッド、およびイベントへのアクセスができます。<br /><br /> 慣例により、項目のプロパティには、項目の子メンバーが含まれます。 そのため、すべての子オブジェクトのプロパティとメソッド (とその子のメンバーを再帰的に) にはアクセスできます。|  
|SCRIPTITEM_ISSOURCE|0x00000004|スクリプトでスクリプトのイベント ハンドラーを持つことができる項目のソースのイベントを示します。|  
|SCRIPTITEM_GLOBALMEMBERS|0x00000008|項目がグローバル プロパティと、スクリプトに関連付けられているメソッドのコレクションであることを示します。 そのメンバーは、グローバル変数とメソッドとして作成されます。|  
|SCRIPTITEM_ISPERSISTENT|0x00000040|エンジンを作成するスクリプトが保存されている場合に、項目が保存されることを示します。|  
|SCRIPTITEM_CODEONLY|0x00000200|コードのみオブジェクトを表し、名前付きの項目を作成するにはメンバーがないことを示します。|  
|SCRIPTITEM_NOCODE|0x00000400|名前付きの項目が追加される名前だけが何も作成することを示します。|  
  
 `pdisp`  
 [in]`IDispatch`の`NamedItem`メソッド、プロパティ、またはイベント ソースを収集するために使用するオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 `HRESULT`。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptAuthor インターフェイス](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)