---
title: "分離シェル アプリケーションを配布します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# 分離シェル アプリケーションを配布します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

分離シェル アプリケーションを作成するためには、Visual Studio と Visual Studio SDK をインストールする必要があります。 その他のユーザーや顧客のコンピューターにアプリケーションを配布するには、分離シェル用の特別な再頒布可能パッケージを含める必要があります。  
  
## 分離シェル アプリケーションを配布するための前提条件  
  
|名前|説明|  
|--------|--------|  
|Visual Studio SDK|開発およびテストの拡張機能のために必要な SDK [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。 SDK を使用して、分離された Visual Studio シェルのインスタンスを作成することもします。<br /><br /> Visual Studio は、SDK の前提条件です。|  
|Microsoft Visual Studio Shell 再頒布可能パッケージの分離|再頒布可能ファイル、Visual Studio のツール環境を構築するときに、セットアップ プログラムに含めることは分離シェルです。 分離 Shell 再頒布可能パッケージには、.NET Framework 4.5 が含まれています。|  
  
## アプリケーションのインストール プログラムを作成します。  
 統合または分離シェル アプリケーションの特殊なインストール プログラムを作成する必要があります。 詳細については、「[分離シェル アプリケーションをインストールします。](../extensibility/installing-an-isolated-shell-application.md)」を参照してください。  
  
## アプリケーションへの更新を許可します。  
 アプリケーションに更新する、Microsoft 更新プログラムまたは社内の更新プログラムのいずれか可能性、インストール プログラムを考慮する必要があります。 更新プログラムに関する詳細については、次を参照してください。 [分離シェル アプリケーションのガイドラインを提供](../extensibility/servicing-guidelines-for-isolated-shell-applications.md)します。