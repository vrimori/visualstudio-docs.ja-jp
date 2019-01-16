---
title: ClickOnce がアプリケーションの更新プログラムを実行する方法 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- updates, ClickOnce
- ClickOnce deployment, updates
- deploying applications [ClickOnce], application updates
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5fc3414660f206aa8f83179e61ed9aa2dcc0098b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53845604"
---
# <a name="how-clickonce-performs-application-updates"></a>ClickOnce がアプリケーションの更新を実行するしくみ
ClickOnce では、アプリケーションの配置マニフェストで指定されたファイル バージョン情報を使用して、アプリケーションのファイルを更新するかどうかを決定します。 ClickOnce と呼ばれる手法を使用して更新プログラムの開始後*ファイル パッチ*アプリケーション ファイルが重複してダウンロードを回避するためにします。  
  
## <a name="file-patching"></a>ファイルの修正  
 アプリケーションを更新するときに ClickOnce ダウンロードしませんのすべてのアプリケーションの新しいバージョンのファイル、ファイルが変更されていない場合。 代わりに、新しいバージョンのマニフェストに署名に対して現在のアプリケーションのアプリケーション マニフェストで指定されたファイルのハッシュの署名と比較します。 ファイルの署名が異なる場合は、ClickOnce は、新しいバージョンをダウンロードします。 署名が一致する場合、ファイルは 1 つのバージョンから、[次へ] をしない変更されました。 この場合は、ClickOnce では、既存のファイルをコピーし、アプリケーションの新しいバージョンでそれを使用します。 この手法により、ClickOnce は、1 つまたは 2 つのファイルが変更された場合でも、再度、アプリケーション全体をダウンロードすることです。  
  
 使用してオンデマンドでダウンロードされたアセンブリ ファイルの修正機能も、<xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A>と<xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A>メソッド。  
  
 Visual Studio を使用してアプリケーションをコンパイルする場合は、プロジェクト全体を再構築するたびにすべてのファイルの新しいハッシュの署名が生成されます。 ここでは、すべてのアセンブリはいくつかのアセンブリだけが変更されていますが、クライアントにダウンロードされます。  
  
 ファイルの修正は、データとしてマークされ、データ ディレクトリに格納するファイルに対しては機能しません。 これらは、ファイルのハッシュの署名に関係なく常にダウンロードします。 データ ディレクトリの詳細については、次を参照してください。 [ClickOnce アプリケーションにおけるローカルおよびリモートのデータにアクセス](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)します。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce の更新方法の選択](../deployment/choosing-a-clickonce-update-strategy.md)   
 [ClickOnce 配置ストラテジの選択](../deployment/choosing-a-clickonce-deployment-strategy.md)