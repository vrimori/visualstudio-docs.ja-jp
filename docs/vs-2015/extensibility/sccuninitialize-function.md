---
title: SccUninitialize 関数 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9cec726eaad2e69ea3adfc850df452c2a06f8059
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547882"
---
# <a name="sccuninitialize-function"></a>SccUninitialize 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[SccUninitialize 関数](https://docs.microsoft.com/visualstudio/extensibility/sccuninitialize-function)します。  
  
この関数は、すべての割り当てと以前の呼び出しによって作成されたオープン接続クリーンアップ、 [SccInitialize](../extensibility/sccinitialize-function.md)ソース管理プラグインをシャット ダウンを準備します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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

