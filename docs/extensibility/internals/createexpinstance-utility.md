---
title: CreateExpInstance ユーティリティ |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bdcb37374c63b96e2169de28c6fe21742024ca98
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128092"
---
# <a name="createexpinstance-utility"></a>CreateExpInstance ユーティリティ
ユーティリティを使用して、CreateExpInstance 作成、リセット、または Visual Studio の実験用インスタンスを削除します。 実験用インスタンスを使用して、デバッグし、基になる製品を変更せずに Visual Studio 拡張機能をテストすることができます。  
  
## <a name="syntax"></a>構文  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### <a name="parameters"></a>パラメーター  
 /作成します。  
 実験用インスタンスを作成します。  
  
 /Reset  
 実験用インスタンスを削除し、新しいものを作成します。  
  
 /Clean  
 実験用インスタンスを削除します。  
  
 /Vsinstance  
 コピーする基本の Visual Studio インスタンスを格納するディレクトリの名前。  
  
 /Rootsuffix  
 実験用インスタンスのディレクトリの名前に追加するサフィックスです。  
  
## <a name="remarks"></a>コメント  
 Visual Studio 拡張機能を使用しているときに、既定の実験用インスタンスを開き、現在の拡張機能のインストールに f5 キーを押してことができます。 実験用インスタンスがない場合は、Visual Studio は、既定の設定のある 1 つを作成します。  
  
 実験用インスタンスの既定の場所は、Visual Studio のバージョン番号に依存します。 たとえば、Visual Studio 2015 での場所は、%localappdata%\Microsoft\VisualStudio\14.0Exp\ ディレクトリの場所にあるすべてのファイルがそのインスタンスの一部と見なされます。 既定の場所にディレクトリ名が変更されない限り、任意の追加の実験用インスタンスは Visual Studio では読み込まれません。  
  
 Visual Studio の実験用インスタンスが開くときに、システム レジストリにアクセスしません。 これは、レジストリ ハイブの実験用のバージョンを使用する Visual Studio の以前のバージョンによって異なります。  
  
 CreateExpInstance ユーティリティには、VsRegEx ユーティリティが置き換えられます。  
  
 次の例では、Visual Studio の既定の実験用インスタンスをリセットします。  
  
 **CreateExpInstance.exe/Reset/vsinstance=14.0 = 14.0/RootSuffix = Exp**  
  
## <a name="see-also"></a>関連項目  
 [VSPackage](../../extensibility/internals/vspackages.md)