---
title: ClickOnce がアプリケーションの更新プログラムを実行する方法 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- updates, ClickOnce
- ClickOnce deployment, updates
- deploying applications [ClickOnce], application updates
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 8011447de248c2dbcdbd513dc4e51106ceb3a568
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548526"
---
# <a name="how-clickonce-performs-application-updates"></a>ClickOnce がアプリケーションの更新を実行するしくみ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[どの ClickOnce 実行アプリケーションの更新プログラム](https://docs.microsoft.com/visualstudio/deployment/how-clickonce-performs-application-updates)します。  
  
ClickOnce では、アプリケーションの配置マニフェストで指定されたファイル バージョン情報を使用して、アプリケーションのファイルを更新するかどうかを決定します。 ClickOnce と呼ばれる手法を使用して更新プログラムの開始後*ファイル パッチ*アプリケーション ファイルが重複してダウンロードを回避するためにします。  
  
## <a name="file-patching"></a>ファイルの修正  
 アプリケーションを更新するときに ClickOnce ダウンロードしませんのすべてのアプリケーションの新しいバージョンのファイル、ファイルが変更されていない場合。 代わりに、新しいバージョンのマニフェストに署名に対して現在のアプリケーションのアプリケーション マニフェストで指定されたファイルのハッシュの署名と比較します。 ファイルの署名が異なる場合は、ClickOnce は、新しいバージョンをダウンロードします。 署名が一致する場合、ファイルは 1 つのバージョンから、[次へ] をしない変更されました。 この場合は、ClickOnce では、既存のファイルをコピーし、アプリケーションの新しいバージョンでそれを使用します。 この手法により、ClickOnce は、1 つまたは 2 つのファイルが変更された場合でも、再度、アプリケーション全体をダウンロードすることです。  
  
 使用してオンデマンドでダウンロードされたアセンブリ ファイルの修正機能も、<xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A>と<xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A>メソッド。  
  
 Visual Studio を使用してアプリケーションをコンパイルする場合は、プロジェクト全体を再構築するたびにすべてのファイルの新しいハッシュの署名が生成されます。 ここでは、すべてのアセンブリはいくつかのアセンブリだけが変更されていますが、クライアントにダウンロードされます。  
  
 ファイルの修正は、データとしてマークされ、データ ディレクトリに格納するファイルに対しては機能しません。 これらは、ファイルのハッシュの署名に関係なく常にダウンロードします。 データ ディレクトリの詳細については、次を参照してください。[ローカルへのアクセスとリモート データには、ClickOnce アプリケーション](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)します。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce の更新方法を選択します。](../deployment/choosing-a-clickonce-update-strategy.md)   
 [ClickOnce 配置ストラテジの選択](../deployment/choosing-a-clickonce-deployment-strategy.md)



