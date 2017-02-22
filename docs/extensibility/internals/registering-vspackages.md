---
title: "Vspackage を登録します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "マネージ VSPackages、登録します。"
  - "登録には、マネージ VSPackages"
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# Vspackage を登録します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] は.pkgdef ファイルについて説明しVSPackage を検索します。  .pkgdef ファイルへの書き込みは。それ以外の場合は追加されたすべての登録情報が含まれています。  マネージ VSPackage は属性をソース・コードに追加し.pkgdef ファイルを生成するために生成されるアセンブリの [CreatePkgDef ユーティリティ](../../extensibility/internals/createpkgdef-utility.md) を実行して登録されます。  
  
## このセクションの内容  
 [VS Shell VSPackage ファイルの場所を指定します。](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 VSPackage の読み込みのパスについて説明します。  
  
 [Vspackage の登録と登録解除しています](../../extensibility/registering-and-unregistering-vspackages.md)  
 VSPackage を登録する方法について説明します。  
  
 [カスタム登録属性を使用した拡張機能の登録](/visual-cpp/misc/using-a-custom-registration-attribute-to-register-an-extension)  
 マネージ VSPackage を配置するために使用できるレジスタのマニフェストを作成する方法について説明します。