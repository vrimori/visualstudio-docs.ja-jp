---
title: CreateExpInstance ユーティリティ |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f1a9f73f396fffe93903f4295428a011c5b5e8d4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55042544"
---
# <a name="createexpinstance-utility"></a>CreateExpInstance ユーティリティ
使用して、 **CreateExpInstance**ユーティリティを作成、リセット、または Visual Studio の実験用インスタンスを削除します。 実験用インスタンスを使用して、デバッグおよび基になる製品を変更することがなく Visual Studio 拡張機能をテストすることができます。  
  
## <a name="syntax"></a>構文  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
## <a name="parameters"></a>パラメーター  
 **/作成**実験用インスタンスを作成します。  
  
 **/Reset**  
 実験用のインスタンスを削除し、新しく作成します。  
  
 **/Clean**  
 実験用インスタンスを削除します。  
  
 **/VSInstance**  
 コピーする基本の Visual Studio インスタンスが含まれているディレクトリの名前。  
  
 **/RootSuffix**  
 実験用インスタンス ディレクトリの名前に付加するサフィックス。  
  
## <a name="remarks"></a>Remarks  
 Visual Studio 拡張機能を使用しているときに既定の実験用インスタンスを開き、現在の拡張機能をインストールして F5 キーを押します。 実験用インスタンスが使用できない場合、既定の設定である Visual Studio を作成します。  
  
 実験用インスタンスの既定の場所は、Visual Studio のバージョン番号に依存します。 たとえば、Visual Studio 2015 の場所は *%localappdata%\Microsoft\VisualStudio\14.0Exp\\*します。 ディレクトリの場所のすべてのファイルは、そのインスタンスの一部と見なされます。 既定の場所にディレクトリ名が変更されない限り、任意の追加の実験用インスタンスは Visual Studio によって読み込まれません。  
  
 Visual Studio 実験用インスタンスを開くときに、システム レジストリにアクセスしません。 これは、レジストリ ハイブの実験用のバージョンを使用すると、Visual Studio の以前のバージョンによって異なります。  
  
 **CreateExpInstance**ユーティリティ置換、 **VsRegEx**ユーティリティ。  
  
 次の例では、Visual Studio の既定の実験用インスタンスをリセットします。  
  
 **CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp**  
  
## <a name="see-also"></a>関連項目  
 [VSPackage](../../extensibility/internals/vspackages.md)