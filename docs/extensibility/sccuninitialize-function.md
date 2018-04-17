---
title: SccUninitialize 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 41cb6b5cec0e0d9bb4c90cc284009ab7fc693912
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sccuninitialize-function"></a>SccUninitialize 関数
この関数は、すべての割り当てと以前の呼び出しによって作成された接続を開く、クリーンアップ、 [SccInitialize](../extensibility/sccinitialize-function.md)ソース管理プラグインをシャット ダウンを準備します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pvContext  
 [in]作成したソース管理プラグインの context 構造体へのポインター、 [SccInitialize](../extensibility/sccinitialize-function.md)です。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|クリーンアップを正常に完了しました。|  
  
## <a name="remarks"></a>コメント  
 ソース管理プラグインはシャット ダウンするを準備し、プラグインが割り当てられている構造体のメモリを解放します。 関数は、プラグインの特定のインスタンスごとに 1 回呼び出されます。 呼び出し、 [SccInitialize](../extensibility/sccinitialize-function.md)この呼び出しの前にします。 プロジェクトを開いたままになっていないへの呼び出し時に`SccUninitialize`です。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)