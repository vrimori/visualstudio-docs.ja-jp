---
redirect_url: shell/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file
title: "使用して分離シェルを変更します。Pkgundef ファイル |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3b4c0f46924c2c828158960a924faa031be0fd14
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>使用して分離シェルを変更します。Pkgundef ファイル
分離シェル アプリケーションから指定されたレジストリ エントリを除外する .pkgundef ファイルを変更することができます。 通常は、初めてコンピューターでは、アプリケーションを起動するとき、Visual Studio shell はコピー Visual Studio の既存のレジストリ エントリを使用、アプリケーションのルート レジストリ キーにします。 これには、現在インストールされている Vspackage への参照が含まれます。  
  
 分離シェル アプリケーションから、特定のレジストリ エントリを除外するには、パッケージ キーのエントリが続くアプリケーション .pkgundef ファイルに追加します。 キーとエントリは、.pkgdef ファイルのように表されますつまり、として [$RootKey$] または [$RootKey$\\*サブキー*] と"*エントリ*"=*値*ここで、*サブキー*に影響を与える、サブキー*エントリ*エントリを削除すると*値*か`""`または`dword:00000000`です。  
  
 除外するには、だけで、レジストリ キーからの複数のエントリは 1 回は、キーを一覧表示、続くを除外するのには、各エントリの行します。  
  
 分離シェル アプリケーションから、全体のレジストリ キーを除外するには、アプリケーション .pkgundef ファイルにキーを追加が、そのキーのレジストリ エントリを指定しないでください。  
  
 .Pkgundef ファイルにコメントを追加することができます。 単一行コメントは、最初の 2 つの文字と 2 つのスラッシュを持たなければなりません。  
  
 例については、削除する、**データベースへの接続**と**Serve r への接続**コマンドを使って、**ツール**] メニューの [行のコメントを解除することができます。  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 行を追加します。  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 アプリケーションの .pkgundef ファイル。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio の機能のパッケージ Guid](../extensibility/package-guids-of-visual-studio-features.md)   
 [分離シェルのカスタマイズ](../extensibility/customizing-the-isolated-shell.md)