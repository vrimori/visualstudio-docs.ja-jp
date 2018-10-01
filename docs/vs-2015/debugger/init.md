---
title: Init |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d394ce2f149be842b42ffe4661cfbc361858bd71
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538849"
---
# <a name="init"></a>Init
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Init](https://docs.microsoft.com/visualstudio/debugger/graphics/init)します。  
  
グラフィックス情報をアクティブにキャプチャしてグラフィックス ログ ファイルに記録するように、グラフィックス診断のアプリ内コンポーネントを準備します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
void Init(  
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `vsgLogGetter`  
 パラメーターとして、`wchar_t` で構成されるバッファーの長さとそのバッファーへのポインターを受け取り、`void` を返す、呼び出し可能なエンティティ (関数、関数ポインター、ラムダ、関数オブジェクトなど)。 呼び出されると、呼び出し可能なエンティティは、グラフィックス情報を記録するために使用されるファイル名を決定し、返される前に指定されたバッファーにファイル名を書き込みます。  
  
## <a name="remarks"></a>Remarks  
 コンストラクターの `Init` パラメーターを `VsgDbg` に指定することで、`bDefaultInit` クラスのインスタンスが構築されると `true` 関数が自動的に呼び出されます。それ以外の場合は、グラフィックス情報をアクティブにキャプチャして記録する前に、`Init` を明示的に呼び出す必要があります。  
  
 `UnInit` を呼び出してアクティブなグラフィックス ログ ファイルを終了して閉じ、`Init` を再度呼び出して、グラフィックス情報をさらにキャプチャして新しいグラフィック ログ ファイルに記録することができます。 この操作を何度でも繰り返して、同じ `VsgDbg` インスタンスを使用して複数の独立したグラフィックス ログ ファイルを作成することができます。  
  
## <a name="see-also"></a>関連項目  
 [UnInit](../debugger/init.md)



