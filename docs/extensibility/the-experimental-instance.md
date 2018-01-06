---
title: "実験用インスタンスの |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
caps.latest.revision: "36"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a656baf951e573a5913960b19c1b583797de090f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="the-experimental-instance"></a>実験用インスタンス
それに変わる可能性があるテストされていないアプリケーションから、Visual Studio 開発環境を保護するためには、VSSDK は、実験に使用できる実験用の領域を提供します。 通常どおり、Visual Studio を使用して新しいアプリケーションを開発するが、この実験用インスタンスを使用して実行します。  
  
 VSIX パッケージを持っているすべてのアプリケーションでは、デバッグ モードで Visual Studio の実験用インスタンスが起動します。  
  
 場合は、特定のソリューションの外部の Visual Studio の実験用インスタンスを開始するは、コマンド ウィンドウで、次のコマンドを実行します。  
  
 "*\<Visual studio インストール パス >*\Common7\IDE\devenv.exe"RootSuffix Exp  
  
> [!NOTE]
>  実験用インスタンスは、下のレジストリに書き込まれます、`<version number>Exp`と`<version number>Exp_Config`ノード。 たとえば、Visual Studio 2015 の実験用のレジストリ領域が  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` および `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 開発しているときに、実験用インスタンスで拡張機能を実行することをお勧めします。 拡張機能を展開するときに、開発用インスタンスで実行されます。 アプリケーションの登録の詳細については、次を参照してください。 [Vspackage の登録](../extensibility/internals/registering-vspackages.md)です。