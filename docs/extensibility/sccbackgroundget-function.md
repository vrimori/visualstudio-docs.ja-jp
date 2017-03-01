---
title: "SccBackgroundGet 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 8bc845c2ef3cb4ece3e52dca272fdc75208e8dbd
ms.lasthandoff: 02/22/2017

---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet 関数
この関数は、ソース管理から各指定されたファイルのユーザー操作なしに取得します。  
  
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
 [in]この操作に関連付けられている一意の値。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-----------|-----------------|  
|SCC_OK|操作が正常に完了しました。|  
|SCC_E_BACKGROUNDGETINPROGRESS|バック グラウンドの取得が既に進行中 (ソース管理プラグインを返すこの同時バッチ処理がサポートしない場合にのみ)。|  
|SCC_I_OPERATIONCANCELED|操作が完了する前に取り消されました。|  
  
## <a name="remarks"></a>コメント  
 この関数は常に、ソース管理プラグインが読み込まれている&1; つから別のスレッドで呼び出されます。 この関数が返すが終了するまでに予期されていませんただし、そのことができます複数回呼び出す複数同時にすべてのファイルのリストにします。  
  
 使用、`dwFlags`引数と同じ、 [SccGet](../extensibility/sccget-function.md)します。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGet](../extensibility/sccget-function.md)
