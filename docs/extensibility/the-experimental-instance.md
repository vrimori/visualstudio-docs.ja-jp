---
title: "実験用インスタンス | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "実験用ビルド"
  - "Vspackages にある、実験用ビルド"
  - "VSIP、実験用ビルド"
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
caps.latest.revision: 36
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 36
---
# 実験用インスタンス
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

変わる可能性があるテストされていないアプリケーションから Visual Studio 開発環境を保護するために、VSSDK は試してみたりする場合に使用できる実験用の領域を提供します。 通常どおり Visual Studio を使用して新しいアプリケーションを開発するが、この実験用インスタンスを使用して実行します。  
  
 VSIX パッケージを持っているすべてのアプリケーションでは、デバッグ モードで Visual Studio の実験用インスタンスが起動します。  
  
 特定のソリューションの外部の Visual Studio の実験用インスタンスを開始する場合は、コマンド ウィンドウで、次のコマンドを実行します。  
  
 "*\< visual studio インストール パス \>*\\Common7\\IDE\\devenv.exe"RootSuffix Exp  
  
> [!NOTE]
>  実験用インスタンスが下にあるレジストリに書き込まれ、 `<version number>Exp` と `<version number>Exp_Config` ノードです。 たとえば、Visual Studio 2015 の実験用のレジストリ領域は  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` および `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 これを開発する際、実験用インスタンスで拡張機能を実行することをお勧めします。 拡張機能を展開するときに、開発用インスタンスで実行されます。 アプリケーションの登録についての詳細については、次を参照してください。 [Vspackage を登録します。](../extensibility/internals/registering-vspackages.md)します。