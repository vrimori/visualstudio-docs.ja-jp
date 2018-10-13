---
title: 実験用インスタンス |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
caps.latest.revision: 37
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 212fc490c26ab66284cf7bdfa4e51946c817266d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49220442"
---
# <a name="the-experimental-instance"></a>実験用インスタンス
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

それに変わる可能性があるテストされていないアプリケーションから、Visual Studio 開発環境を保護するためには、VSSDK は実験に使用できる実験用の領域を提供します。 通常どおり、Visual Studio を使用して新しいアプリケーションを開発するが、この実験用インスタンスを使用して実行します。  
  
 VSIX パッケージを持っているすべてのアプリケーションでは、デバッグ モードで Visual Studio の実験用インスタンスを起動します。  
  
 特定のソリューションの外部の Visual Studio の実験用インスタンスを開始する場合は、コマンド ウィンドウで次のコマンドを実行します。  
  
 "*\<Visual studio インストール パス >* \Common7\IDE\devenv.exe"RootSuffix Exp  
  
> [!NOTE]
>  実験用インスタンスが下のレジストリに書き込まれる、`<version number>Exp`と`<version number>Exp_Config`ノード。 たとえば、Visual Studio 2015 の実験用のレジストリ領域は  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` および `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 開発しているときに、実験用インスタンスで、拡張機能を実行することをお勧めします。 拡張機能をデプロイするときに、開発用インスタンスで実行されます。 アプリケーションの登録の詳細については、次を参照してください。 [Vspackage の登録](../extensibility/internals/registering-vspackages.md)します。

