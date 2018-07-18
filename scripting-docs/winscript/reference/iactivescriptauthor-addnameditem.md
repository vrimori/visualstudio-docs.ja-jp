---
title: IActiveScriptAuthor::AddNamedItem |Microsoft ドキュメント
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
ms.openlocfilehash: 83d2597f8468bb97d20da655a56a751191ec4b55
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645612"
---
# <a name="iactivescriptauthoraddnameditem"></a>IActiveScriptAuthor::AddNamedItem
スクリプト エンジンの名前空間を作成するには、ルート レベルの項目の名前を追加します。 A*ルート レベルの項目*プロパティとメソッドを持つことができるし、イベント ソースを持つことができるオブジェクトです。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT AddNamedItem(  
   LPCOLESTR          pszName,  
   DWORD              dwFlags,  
   IDispatch          *pdisp  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszName`  
 [in]スクリプトで表示される項目の名前。 名前には、一意、持続可能なを指定する必要があります。  
  
 `dwFlags`  
 [in]名前付きの項目に関連付けられているフラグです。 次の値の組み合わせが可能です。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|SCRIPTITEM_ISVISIBLE|0x00000002|項目の名前が、スクリプトの名前空間で使用できることを示します。 これにより、アイテムのプロパティ、メソッド、およびイベントにアクセスできます。<br /><br /> 慣例により、項目のプロパティには、アイテムの子メンバーが含まれます。 そのため、すべての子オブジェクトのプロパティとメソッド (とその子メンバーを再帰的に) にアクセスできます。|  
|SCRIPTITEM_ISSOURCE|0x00000004|スクリプトでスクリプトのイベント ハンドラーを持つことができる項目のソースのイベントを示します。|  
|SCRIPTITEM_GLOBALMEMBERS|0x00000008|項目がグローバル プロパティと、スクリプトに関連付けられているメソッドのコレクションであることを示します。 そのメンバーは、グローバル変数およびメソッドとして作成されます。|  
|SCRIPTITEM_ISPERSISTENT|0x00000040|エンジンを作成するスクリプトが保存されている場合に、項目が保存されることを示します。|  
|SCRIPTITEM_CODEONLY|0x00000200|名前付きの項目を表すコード専用のオブジェクトを作成するにはメンバーがないことを示します。|  
|SCRIPTITEM_NOCODE|0x00000400|名前付きの項目が追加される名前だけを作成するものがあることを示します。|  
  
 `pdisp`  
 [in]`IDispatch`の`NamedItem`メソッド、プロパティ、またはイベント ソースを収集するために使用できるオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 `HRESULT`。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptAuthor インターフェイス](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)