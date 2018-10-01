---
title: 実験用インスタンス |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: 3d819be41806e075de23dbfb5b5b3cded5bbeb40
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539220"
---
# <a name="the-experimental-instance"></a>実験用インスタンス
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[、実験用インスタンス](https://docs.microsoft.com/visualstudio/extensibility/the-experimental-instance)します。  
  
それに変わる可能性があるテストされていないアプリケーションから、Visual Studio 開発環境を保護するためには、VSSDK は実験に使用できる実験用の領域を提供します。 通常どおり、Visual Studio を使用して新しいアプリケーションを開発するが、この実験用インスタンスを使用して実行します。  
  
 VSIX パッケージを持っているすべてのアプリケーションでは、デバッグ モードで Visual Studio の実験用インスタンスを起動します。  
  
 特定のソリューションの外部の Visual Studio の実験用インスタンスを開始する場合は、コマンド ウィンドウで次のコマンドを実行します。  
  
 "*\<Visual studio インストール パス >* \Common7\IDE\devenv.exe"RootSuffix Exp  
  
> [!NOTE]
>  実験用インスタンスが下のレジストリに書き込まれる、`<version number>Exp`と`<version number>Exp_Config`ノード。 たとえば、Visual Studio 2015 の実験用のレジストリ領域は  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` および `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 開発しているときに、実験用インスタンスで、拡張機能を実行することをお勧めします。 拡張機能をデプロイするときに、開発用インスタンスで実行されます。 アプリケーションの登録の詳細については、次を参照してください。 [Vspackage の登録](../extensibility/internals/registering-vspackages.md)します。

