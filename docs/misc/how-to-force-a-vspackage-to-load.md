---
title: "方法: VSPackage を強制的に読み込む | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackage、強制的な読み込み"
  - "VSPackage、読み込み"
ms.assetid: 05f4dc3f-3c9a-45ea-96da-986553b5c5f2
caps.latest.revision: 20
caps.handback.revision: 20
manager: "douge"
---
# 方法: VSPackage を強制的に読み込む
VSPackage は通常プロセスを完了するに含まれる機能が必要な場合にのみ読み込まれます。  ただし場合によってはVSPackage別の VSPackage の読み込み必要があります。  たとえばVSPackage 簡易は CMDUIContext として使用できないプログラミングのコンテキストではVSPackage を読み込むことがあります。  
  
 読み込むにはVSPackage を強制的に <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> のメソッドを使用できます。  
  
### VSPackage の読み込み  
  
-   別の VSPackage を読み込ませる VSPackage の <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> のメソッドに次のコードを挿入します :  
  
     [!code-cs[ForceVSPackageLoad#01](../misc/codesnippet/CSharp/how-to-force-a-vspackage-to-load_1.cs)]  
  
     VSPackage を初期化するときは`PackageToBeLoaded` の読み込み。  
  
## 信頼性の高いプログラミング  
 強制的にはVSPackage の読み込みの通信に使用する必要があります。  代わりに、[使用して、サービスを提供します。](../extensibility/using-and-providing-services.md) を使用してください。  
  
## 参照  
 [Vspackage を管理します。](../extensibility/managing-vspackages.md)   
 [Vspackages にあります。](../extensibility/internals/vspackages.md)