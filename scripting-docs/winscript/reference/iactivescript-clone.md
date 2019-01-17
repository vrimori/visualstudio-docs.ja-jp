---
title: Iactivescript::clone |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Clone
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Clone
ms.assetid: aa000b2a-7085-448d-a422-f7adac7851cb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 084da486d2e5831176130ccd080b9e09a80c9bcc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093666"
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
現在のスクリプト エンジン (すべて現在の実行状態)、マイナス記号を現在のスレッドでサイトを持たない読み込まれたスクリプト エンジンを返すことを複製します。 この新しいスクリプト エンジンのプロパティは、元のスクリプト エンジンであるかどうか、初期化済み状態に移行されたプロパティに同じになります。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppscript`  
 [out]ポインターを受け取る変数のアドレス、 [IActiveScript](../../winscript/reference/iactivescript.md)複製されたスクリプト エンジンのインターフェイス。 ホストは、サイトと呼び出しを作成する必要があります、 [iactivescript::setscriptsite](../../winscript/reference/iactivescript-setscriptsite.md)初期化済み状態にするには、新しいスクリプト エンジン メソッドと、そのため、使用可能な。  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_NOTIMPL`|このメソッドはサポートされていません。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`E_UNEXPECTED`|呼び出しが予期されていませんでした (たとえば、スクリプト エンジンがされていないされて読み込まれるまたは初期化) します。|  
  
## <a name="remarks"></a>Remarks  
 `IActiveScript::Clone`メソッドは、最適化された`IPersist*::Save`、 `CoCreateInstance`、および`IPersist*::Load`ので、新しいスクリプト エンジンの状態、元のスクリプト エンジンの状態の保存し、新しいスクリプト エンジンに読み込まれるかに同じにする必要があります。 名前付きの項目は、複製されたスクリプト エンジンで複製されますが、各項目の特定のオブジェクト ポインターが破棄されているとは、 [iactivescriptsite::getiteminfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)メソッド。 これにより、使用するスレッドごとのエントリ ポイント (アパートメント モデル) が同じオブジェクト モデルです。  
  
 このメソッドは、同じスクリプトの複数のインスタンスを実行できるマルチ スレッド サーバー ホストに使用されます。 スクリプト エンジンが返す可能性があります`E_NOTIMPL`、ホストが永続的な状態を複製して、スクリプト エンジンの新しいインスタンスを作成して同じ結果を得ることができる場合、`IPersist*`インターフェイス。  
  
 このメソッドは、ホスト オブジェクトまたはベース以外の吹き出しでベース以外のスレッドから呼び出すことができます、 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)インターフェイス。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScript](../../winscript/reference/iactivescript.md)