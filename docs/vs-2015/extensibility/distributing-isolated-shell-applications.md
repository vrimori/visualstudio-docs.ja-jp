---
title: 分離シェル アプリケーションの配布 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7388a5b723b5346f1f653024215c16ba474fa48a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547486"
---
# <a name="distributing-isolated-shell-applications"></a>分離シェル アプリケーションの配布
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[分離シェル アプリケーションを配布する](https://docs.microsoft.com/visualstudio/extensibility/distributing-isolated-shell-applications)します。  
  
分離シェル アプリケーションを作成するには、Visual Studio と Visual Studio SDK をインストールする必要があります。 その他のユーザーやお客様のマシンにアプリケーションを配布するには、分離シェルの特別な再頒布可能パッケージを含める必要があります。  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>分離シェル アプリケーションを配布するための前提条件  
  
|名前|説明|  
|----------|-----------------|  
|Visual Studio SDK|開発とテストの拡張機能が必要 SDK[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。 Visual Studio 分離シェルのインスタンスを作成するのに、SDK を使用することもできます。<br /><br /> Visual Studio では、SDK の前提条件です。|  
|Microsoft Visual Studio 分離シェルの再頒布可能パッケージ|再頒布可能ファイル、Visual Studio のツール環境をビルドするときに、セットアップ プログラムに含めることは分離シェルです。 分離シェルの再頒布可能パッケージには、.NET Framework 4.5 が含まれています。|  
  
## <a name="creating-an-installation-program-for-the-application"></a>アプリケーションのインストール プログラムを作成します。  
 統合または分離シェル アプリケーションの特殊なインストール プログラムを作成する必要があります。 詳細については、次を参照してください。[分離シェル アプリケーションをインストールする](../extensibility/installing-an-isolated-shell-application.md)します。  
  
## <a name="allowing-for-updates-to-your-application"></a>アプリケーションを更新することができます。  
 インストール プログラム、アプリケーションが更新されること、Microsoft 更新プログラムまたは会社の更新プログラムのいずれか可能性を考慮する必要があります。 更新プログラムの詳細については、次を参照してください。[分離シェル アプリケーションのサービスのガイドライン](../extensibility/servicing-guidelines-for-isolated-shell-applications.md)します。

