---
title: POPLISTFUNC |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f35ae28a1a231721d5ee5616a3b075737c24e629
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54982235"
---
# <a name="poplistfunc"></a>POPLISTFUNC
このコールバックが渡される、 [SccPopulateList](../extensibility/sccpopulatelist-function.md) IDE でファイルまたはディレクトリの一覧を更新するソース管理プラグインが使用されます (に渡されることも、`SccPopulateList`関数)。  
  
 ユーザーが選択したときに、**取得**IDE では、コマンドと、ユーザーが得られるすべてのファイルの一覧ボックスが表示されます。 残念ながら、IDE には、ユーザーが取得可能性があります。 すべてのファイルの正確な一覧がわからないこのリストのみプラグインがあります。 その他のユーザーには、ソース コード コントロール プロジェクトにファイルが追加、一覧で、これらのファイルが表示されますが、IDE で認識されていないこと。 IDE は、ユーザーが取得できると思われるファイルの一覧を作成します。 呼び出しをユーザーには、この一覧が表示されます、前に、 [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,`ソース管理プラグインを提供を追加し、ファイルを一覧から削除します。  
  
## <a name="signature"></a>署名  
 ソース管理プラグインは、次のプロトタイプで、IDE 実装関数を呼び出すことによって、リストを変更します。  
  
```cpp  
typedef BOOL (*POPLISTFUNC) (  
   LPVOID pvCallerData,  
   BOOL fAddRemove,  
   LONG nStatus,  
   LPSTR lpFileName  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 pvCallerData  
 `pvCallerData`に呼び出し元 (IDE) によって渡されるパラメーター、 [SccPopulateList](../extensibility/sccpopulatelist-function.md)します。 ソース管理プラグインは、このパラメーターの内容に関して何も想定してください。  
  
 fAddRemove  
 場合`TRUE`、`lpFileName`ファイル、ファイルの一覧に追加する必要があります。 場合`FALSE`、`lpFileName`ファイル、ファイルの一覧から削除する必要があります。  
  
 nStatus  
 ステータス`lpFileName`(の組み合わせ、`SCC_STATUS`ビット; を参照してください[ファイルの状態コード](../extensibility/file-status-code-enumerator.md)詳細については)。  
  
 lpFileName  
 一覧から追加または削除するファイル名の完全なディレクトリ パス。  
  
## <a name="return-value"></a>戻り値  
  
|[値]|説明|  
|-----------|-----------------|  
|`TRUE`|プラグインを続行できますこの関数を呼び出します。|  
|`FALSE`|(メモリ不足) などの IDE 側で問題が発生しました。 操作は、プラグインの場合に停止する必要があります。|  
  
## <a name="remarks"></a>Remarks  
 ソース管理プラグインを追加したりファイルの一覧から削除しようとする各ファイルを渡して、この関数の呼び出しが、`lpFileName`します。 `fAddRemove`フラグは、一覧に追加する新しいファイルまたは古いファイルを削除することを示します。 `nStatus`パラメーターは、ファイルの状態。 SCC プラグインには、追加して、ファイルの削除が完了したら、それを返します、 [SccPopulateList](../extensibility/sccpopulatelist-function.md)呼び出します。  
  
> [!NOTE]
>  `SCC_CAP_POPULATELIST`機能ビットは Visual Studio に必要です。  
  
## <a name="see-also"></a>関連項目  
 [IDE によって実装されるコールバック関数](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [ファイルの状態コード](../extensibility/file-status-code-enumerator.md)