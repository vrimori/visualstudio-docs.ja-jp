---
title: IActiveScript::Clone |Microsoft ドキュメント
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
ms.openlocfilehash: 4b0b83bcf86bcc56701d11f22640df966334697b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641592"
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
現在のスクリプト エンジン (すべて現在の実行状態)、マイナス記号を現在のスレッド内のサイトを持たない読み込まれたスクリプト エンジンを返すのクローンを作成します。 この新しいスクリプト エンジンのプロパティは、元のスクリプト エンジンようになります。 初期化済みの状態に遷移しましたされたかどうかのプロパティと同じになります。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppscript`  
 [out]ポインターを受け取る変数のアドレス、 [IActiveScript](../../winscript/reference/iactivescript.md)クローンとして作成されたスクリプト エンジンのインターフェイスです。 ホストは、サイトと呼び出しを作成する必要があります、 [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)初期化状態になる前に、新しいスクリプト エンジンのメソッドと、そのため、使用可能です。  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_NOTIMPL`|このメソッドはサポートされていません。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`E_UNEXPECTED`|呼び出しが予期されていませんでした (たとえば、スクリプト エンジンがされていないされて読み込まれたまたは初期化) します。|  
  
## <a name="remarks"></a>コメント  
 `IActiveScript::Clone`メソッドは、最適化された`IPersist*::Save`、 `CoCreateInstance`、および`IPersist*::Load`ので、新しいスクリプト エンジンの状態は同じはず元のスクリプト エンジンの状態が保存され、新しいスクリプト エンジンに読み込まれたかのようです。 名前付きアイテムが、複製されたスクリプト エンジンで複製されますが、項目ごとに特定のオブジェクトのポインターは忘れで取得した、 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)メソッドです。 これにより、スレッドごとのエントリ ポイント (アパートメント モデル) 使用すると、同一のオブジェクト モデルです。  
  
 このメソッドは、同じスクリプトの複数のインスタンスを実行できるマルチ スレッド サーバー ホストに使用されます。 スクリプト エンジンが返す可能性があります`E_NOTIMPL`、ホストが永続的な状態を複製し、スクリプト エンジンでの新しいインスタンスを作成して同じ結果を得ることができる場合、`IPersist*`インターフェイスです。  
  
 このメソッドは、ホスト オブジェクトまたはベース以外吹き出しの結果として得られることがなくベース以外のスレッドから呼び出すことができます、 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)インターフェイスです。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScript](../../winscript/reference/iactivescript.md)