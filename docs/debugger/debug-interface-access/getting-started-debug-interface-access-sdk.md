---
title: はじめに (Debug Interface Access SDK) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- .dbg files
- DBG files
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e5cfcad351f19f48678d575e11b074375c6aaadc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887296"
---
# <a name="getting-started-debug-interface-access-sdk"></a>はじめに (Debug Interface Access SDK)
デバッグ インターフェイスへのアクセス (DIA) SDK では、説明のドキュメントと DIA API を使用する方法を示すサンプルを提供します。 DIA sdk インターフェイスとメソッドを使用して .pdb と .dbg ファイルを開き、シンボル、値、属性、アドレス、およびその他のデバッグ情報のコンテンツを検索するカスタム アプリケーションを開発します。 この SDK には、C++ アプリケーションで見られる記号に関連付けられているプロパティの参照テーブルも提供します。  
  
 最適な DIA SDK を使用するには、は、次のようにについて理解する必要があります。  
  
- C++ プログラミング言語  
  
- COM プログラミング  
  
- Visual Studio 統合開発環境 (IDE) のサンプルのコンパイル  
  
  DIA SDK は、通常、Visual Studio をインストールし、その既定の場所は *[ドライブ]* \Program Files\Microsoft Visual Studio 9.0\DIA SDK。 インストールの一環として、DIA SDK を実装すると、msdia90.dll は自動的に登録を含めるので、これを使用するために必要な`dia2.h`プログラムへのリンクで`diaguids.lib`します。  
  
  ヘッダー: include\dia2.h  
  
  ライブラリ: lib\diaguids.lib  
  
  DLL: bin\msdia80.dll  
  
  IDL: idl\dia2.idl  
  
## <a name="in-this-section"></a>このセクションの内容  
 [概要](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 中の基本的なアーキテクチャをレビューします。  
  
 [.Pdb ファイルの照会](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 DIA API を使用して、.pdb ファイルを照会する方法の手順を説明します。  
  
## <a name="see-also"></a>関連項目  
 [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)