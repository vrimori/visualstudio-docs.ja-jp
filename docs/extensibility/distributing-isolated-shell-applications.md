---
redirect_url: shell/distributing-isolated-shell-applications
title: "分離シェル アプリケーションを配布する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a40d2b8c108d7180ffc68ac2eee6811d49b21c08
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="distributing-isolated-shell-applications"></a>分離シェル アプリケーションを配布します。
分離シェル アプリケーションを作成するのには、Visual Studio および Visual Studio SDK をインストールする必要があります。 その他のユーザーや顧客のマシンにアプリケーションを配布するには、分離シェルの特別な再頒布可能パッケージを含める必要があります。  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>分離シェル アプリケーションを配布するための前提条件  
  
|名前|説明|  
|----------|-----------------|  
|Visual Studio SDK|開発およびテストの拡張機能にする必要があります SDK[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。 SDK を使用して、Visual Studio 分離シェルの独自のインスタンスを作成することができますも。<br /><br /> Visual Studio は、SDK の前提条件です。|  
|Microsoft Visual Studio 分離シェルの再頒布可能パッケージ|再頒布可能パッケージ、Visual studio ツール環境をビルドするときに、セットアップ プログラムに含めることは分離シェルです。 分離シェル再頒布可能パッケージには、.NET Framework 4.5 が含まれています。|  
  
## <a name="creating-an-installation-program-for-the-application"></a>アプリケーションのインストール プログラムを作成します。  
 統合または分離シェル アプリケーションの特殊なインストール プログラムを作成する必要があります。 詳細については、次を参照してください。[分離シェル アプリケーションをインストールする](../extensibility/installing-an-isolated-shell-application.md)です。  
  
## <a name="allowing-for-updates-to-your-application"></a>アプリケーションへの更新を許可します。  
 インストール プログラムは、アプリケーションが更新されること、Microsoft 更新プログラムまたは会社の更新プログラムのいずれかの考慮事項許可する必要があります。 更新プログラムの詳細については、次を参照してください。[分離シェル アプリケーションのサービスのガイドライン](../extensibility/servicing-guidelines-for-isolated-shell-applications.md)です。