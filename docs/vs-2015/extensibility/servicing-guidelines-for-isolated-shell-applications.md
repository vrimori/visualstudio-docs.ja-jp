---
title: 分離シェル アプリケーションのサービスのためのガイドライン |Microsoft Docs
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
- Visual Studio Shell integrated mode, serviceability
- Shell integrated mode [Visual Studio], serviceability
ms.assetid: 747d1a47-b8b3-4e8b-93c0-768724be48f2
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dff7d9349e5081fa0e8ab64bfd32c90b83f19de3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544678"
---
# <a name="servicing-guidelines-for-isolated-shell-applications"></a>ガイドライン分離シェル アプリケーションの提供
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[分離シェル アプリケーションのサービスのガイドライン](https://docs.microsoft.com/visualstudio/extensibility/servicing-guidelines-for-isolated-shell-applications)します。  
  
Visual Studio 分離シェル アプリケーションを配布するときに、ソフトウェア更新プログラムをインストールした後、アプリケーションに対して提供する必要があります。 これを行うには、Microsoft インストーラー (MSI) ファイルを使用して、アプリケーションをインストールする必要があります。 この種類のインストールは、Web で再配布するマイクロソフトによって提供されるソフトウェア更新プログラムをダウンロードして、顧客をカスタムの介入なしで使用できます。  
  
## <a name="servicing-requirements"></a>サービスの要件  
 分離シェルのインストールが、インストール プログラムが次の 3 つの条件を満たしていることを確認して更新プログラムを許可できますを保証できます。  
  
### <a name="redistribute-by-using-an-msi"></a>MSI を使用して、再配布します。  
 MSI を使用して、アプリケーションを再配布する必要があります、アプリケーションがクライアント コンピューターの物理的な場所を持つため、MSI は、製品の id を保持し、それを確認してください。 マージ モジュール (.msm ファイル) は、このような保証を指定しないは使用できません。  
  
### <a name="accounting-for-custom-actions"></a>カスタム アクションのアカウンティング  
 カスタム アクションには、インストーラー プログラムでの非標準インストール ディレクティブがあります。 カスタム アクションは、ファイルの場所、レジストリ設定、ユーザー設定、またはその他のインストール項目などのパラメーターを変更します。 カスタム アクションは、インストール時にデータを操作する可能性があります。  
  
 インストール プログラムのカスタム アクションを使用する場合は、すべてのインストール時のカスタム アクションが、ユーザーがアプリケーションをアンインストールするときに、操作を元に戻すに対応するカスタム アクションを持つ必要があることを確認する必要があります。 対応するため、インストール プログラムは失敗では、カスタム アクションをアンインストールする場合、アプリケーションの削除はのままに部分的にインストールされています。  
  
-   ソフトウェア更新プログラムがこれらのバージョンを変更したり、ハッシュ値と、ファイルまたはハッシュの値の特定のバージョンに依存するカスタム アクションは失敗します。 この場合、カスタム アクションは、これらの値を手動で更新する必要があります。 その他の問題では、バージョンのファイルまたはハッシュの値は製品のバージョン間で共有されている場合に発生します。 可能な場合は、この依存関係を回避します。  
  
### <a name="accounting-for-shared-files"></a>共有ファイルのアカウンティング  
 共有ファイルと同じ名前し、複数の製品で同じ場所にインストールされます。 これらの製品は、バージョン、在庫管理単位 (SKU)、またはその両方で異なる場合があり、製品は、特定のコンピューターで共存できます。 ただし、共有ファイルは、いくつかの理由のサービスの問題を作成します。  
  
-   共有ファイルを更新すると、1 つのアプリケーションの更新プログラムが更新されていない 2 つ目のアプリケーションによって使用されるファイルのバージョンを変更するためにアプリケーション互換性の問題が発生することができます。 ファイルを共有する製品のインストーラーは、共有ファイルへの参照をカウントします。 そのため、製品をアンインストールしても、共有ファイルのインストール済みのインスタンスのカウントをデクリメントする操作以外には影響しません。  
  
-   Quick Fix Engineering (QFE) インストーラーには、QFE インストーラー サービスを提供する製品のバージョンのファイルのバージョンが元に戻します。 このプロセスは、可能性のある更新された共有ファイルが提供するアプリケーションを中断します。

