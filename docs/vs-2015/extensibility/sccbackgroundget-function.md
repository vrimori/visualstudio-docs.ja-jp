---
title: SccBackgroundGet 関数 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a2b56f2a094a736e93d9bef7074939855d0e60ab
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730565"
---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

この関数は、ソース管理から各指定されたファイルのユーザーの操作なしで取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccBackgroundGet(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LONG    dwFlags,  
   LONG    dwBackgroundOperationID  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pContext  
 [in]ソース管理プラグインのコンテキストのポインター。  
  
 nFiles  
 [in]指定されたファイルの数、`lpFileNames`配列。  
  
 lpFileNames  
 [入力、出力]取得するファイルの名前の配列。  
  
> [!NOTE]
>  名前は、完全修飾のローカル ファイル名である必要があります。  
  
 dwFlags  
 [in]コマンドのフラグ (`SCC_GET_ALL`、 `SCC_GET_RECURSIVE`)。  
  
 dwBackgroundOperationID  
 [in]この操作に関連付けられた一意の値。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|操作が正常に完了しました。|  
|SCC_E_BACKGROUNDGETINPROGRESS|バック グラウンド取得が既に進行中 (ソース管理プラグインを返すこの同時バッチ操作がサポートしない場合にのみ)。|  
|SCC_I_OPERATIONCANCELED|操作が完了する前に取り消されました。|  
  
## <a name="remarks"></a>Remarks  
 この関数は常にソース管理プラグインが読み込まれているものと異なるスレッドで呼び出されます。 この関数は戻りますが完了するまでは必要ありません。ただし、その複数回と共に呼び出せる複数同時にすべてのファイルのリスト。  
  
 使用、`dwFlags`引数が同じ、 [SccGet](../extensibility/sccget-function.md)します。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGet](../extensibility/sccget-function.md)

