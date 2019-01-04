---
title: SccUninitialize 関数 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 64e894fe2ce1eaf6f74ed01d2e76f7ce3d33f9fb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53949642"
---
# <a name="sccuninitialize-function"></a>SccUninitialize 関数
この関数は、すべての割り当てと以前の呼び出しによって作成されたオープン接続クリーンアップ、 [SccInitialize](../extensibility/sccinitialize-function.md)ソース管理プラグインをシャット ダウンを準備します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pvContext  
 [in]作成したソース コントロールのプラグインの context 構造体へのポインター、 [SccInitialize](../extensibility/sccinitialize-function.md)します。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|クリーンアップを正常に完了しました。|  
  
## <a name="remarks"></a>Remarks  
 プラグインのソース コントロールはシャット ダウンするための準備と構造体のプラグインが割り当てたメモリを解放します。 関数は、プラグインの特定のインスタンスごとに 1 回呼び出されます。 呼び出し、 [SccInitialize](../extensibility/sccinitialize-function.md)この呼び出しの前にします。 プロジェクトは開いたままになっていないへの呼び出し時に`SccUninitialize`します。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)