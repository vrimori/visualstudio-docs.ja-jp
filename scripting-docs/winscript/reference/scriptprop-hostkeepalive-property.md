---
title: SCRIPTPROP_HOSTKEEPALIVE プロパティ |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: bfa199f2-28ba-4320-bc0f-2320fad018bd
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a39ae7100c5567d2b03b7998077b20b1078810aa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734142"
---
# <a name="scriptprophostkeepalive-property"></a>SCRIPTPROP_HOSTKEEPALIVE プロパティ
スクリプト エンジンを未解決の参照がある場合は、完全に機能保持するかどうかを指定するために使用します。  
  
 使用して[IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md)にこのプロパティを設定する`true`です。 このプロパティ設定されている場合`true`、スクリプト エンジン自体にするかを少なくとも 1 つの未解決の参照がある限り、スクリプト エンジンが完全に機能を保持する`IDispatch`スクリプトを使用して作成された JavaScript オブジェクトへのポインターエンジン。 このプロパティに設定するときに`true`、明示的に閉じるかを使用して、スクリプト エンジンをリセットする必要があります、 [IActiveScript::Close](../../winscript/reference/iactivescript-close.md)または[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)メソッドです。 スクリプト オブジェクトへの最後の参照のリリースでは、スクリプト エンジンをシャット ダウンします。  
  
## <a name="syntax"></a>構文  
  
```  
#define SCRIPTPROP_HOSTKEEPALIVE 0x70000004  
```  
  
## <a name="requirements"></a>要件  
 と共にインストールされる activscp.idl のバージョンでのみこのプロパティが表示されます[!INCLUDE[win8](../../javascript/includes/win8-md.md)]で Internet Explorer 8 用の KB 2707082 で[!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)]、または Internet Explorer 9 のサポート技術情報 2722913[!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)]または[!INCLUDE[vista_first](../../winscript/reference/includes/vista-first-md.md)]です。