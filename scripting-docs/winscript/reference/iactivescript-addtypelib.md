---
title: "IActiveScript::AddTypeLib |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.AddTypeLib
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_AddTypeLib
ms.assetid: 8e507ea8-c80a-471c-b482-ae753c6e8595
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2be7cf033b4b5dd4d99b19a3b71ed53e32af855
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptaddtypelib"></a>IActiveScript::AddTypeLib
スクリプトの名前空間をタイプ ライブラリを追加します。 これがに似ていますが、 `#include` C/C++ のディレクティブ。 これにより、一連のクラス定義などの定義済みの項目`typedefs`、名前付き定数をスクリプトに使用可能なランタイム環境に追加するとします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT AddTypeLib(  
    REFGUID guidTypeLib,  // CLSID of type library  
    DWORD dwMaj,          // major version number  
    DWORD dwMin,          // minor version number  
    DWORD dwFlags         // option flags  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `guidTypeLib`  
 [in]追加するタイプ ライブラリの CLSID。  
  
 `dwMaj`  
 [in]メジャー バージョン番号。  
  
 `dwMin`  
 [in]マイナー バージョン番号。  
  
 `dwFlags`  
 [in]オプションのフラグです。 以下を指定できます。  
  
|値|説明|  
|-----------|-------------|  
|SCRIPTTYPELIB_ISCONTROL|タイプ ライブラリでは、ホストによって使用される ActiveX コントロールについて説明します。|  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引数が無効です。|  
|`E_UNEXPECTED`|呼び出しが予期されていませんでした (たとえば、スクリプト エンジンがされていないされて読み込まれたまたは初期化) します。|  
|`TYPE_E_CANTLOADLIBRARY`|指定したタイプ ライブラリを読み込むことができませんでした。|  
  
## <a name="see-also"></a>関連項目  
 [IActiveScript](../../winscript/reference/iactivescript.md)