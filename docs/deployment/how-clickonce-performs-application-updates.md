---
title: "ClickOnce がアプリケーションの更新プログラムを実行する方法 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
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
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 6ee199aa98c0c5b72a5693c840b892929e55477a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-clickonce-performs-application-updates"></a>ClickOnce がアプリケーションの更新を実行するしくみ
ClickOnce では、アプリケーションの配置マニフェストで指定されたファイル バージョン情報を使用して、アプリケーションのファイルを更新するかどうかを決定します。 ClickOnce と呼ばれる手法を使用して更新プログラムの開始後*ファイル パッチ*をアプリケーション ファイルが重複してダウンロードを回避します。  
  
## <a name="file-patching"></a>ファイル パッチ  
 アプリケーションを更新するときに ClickOnce をダウンロードしませんのすべてのアプリケーションの新しいバージョンのファイルのファイルが変更された場合を除き、します。 代わりに、新しいバージョンのマニフェストに署名に対して現在のアプリケーションのアプリケーション マニフェストで指定されたファイルのハッシュ署名を比較します。 ファイルの署名が異なる場合は、ClickOnce は、新しいバージョンをダウンロードします。 署名が一致する場合、ファイルが変更されていない 1 つのバージョンから、次にします。 この場合、ClickOnce では、既存のファイルをコピーし、新しいバージョンのアプリケーションで使用します。 この手法により、ClickOnce は、1 つまたは 2 つのファイルが変更された場合でも、アプリケーション全体をダウンロードすることです。  
  
 使用してオンデマンドでダウンロードされたアセンブリに対しても機能ファイルが修正プログラム、<xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A>と<xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A>メソッドです。  
  
 Visual Studio を使用して、アプリケーションをコンパイルする場合、プロジェクト全体を再構築するときにすべてのファイルに対して新しいハッシュ署名が生成されます。 ここでは、すべてのアセンブリはいくつかのアセンブリだけが変更された可能性がありますが、クライアントにダウンロードされます。  
  
 データとしてマークされ、データ ディレクトリに格納されているファイルのファイルが修正プログラムは機能しません。 これらは、ファイルのハッシュの署名に関係なく常にダウンロードします。 データ ディレクトリの詳細については、次を参照してください。[ローカルへのアクセスと ClickOnce アプリケーションでのリモート データ](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)です。  
  
## <a name="see-also"></a>参照  
 [ClickOnce の更新方法の選択](../deployment/choosing-a-clickonce-update-strategy.md)   
 [ClickOnce 配置ストラテジの選択](../deployment/choosing-a-clickonce-deployment-strategy.md)