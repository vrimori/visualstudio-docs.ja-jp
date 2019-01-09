---
title: -ResetSkipPkgs (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a892902e129044549f781648d34bf058bf6eae9b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53853633"
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
問題のある VSPackage の読み込みを避けるためにユーザーによって VSPackage に追加された、読み込みを省略するためのオプションをすべてクリアします。その後、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] を起動させます。

## <a name="syntax"></a>構文

```cmd
Devenv /ResetSkipPkgs
```

## <a name="remarks"></a>コメント
 SkipLoading タグがあると、VSPackage の読み込みが無効になります。タグをクリアすると、VSPackage の読み込みが再度有効になります。

## <a name="example"></a>例
 次の例では、すべての SkipLoading タグをクリアします。

```cmd
Devenv.exe /ResetSkipPkgs
```

## <a name="see-also"></a>「

- [Devenv コマンドライン スイッチ](../../ide/reference/devenv-command-line-switches.md)