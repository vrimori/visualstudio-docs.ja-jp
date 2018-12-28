---
title: VS Shell 配置
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 663e706dba9ec7b6479e3e9360ef8aa2d12b1400
ms.sourcegitcommit: 159ed9d4f56cdc1dff2fd19d9dffafe77e46cd4e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2018
ms.locfileid: "53739498"
---
# <a name="vs-shell-deployment"></a>VS Shell 配置

分離のシェルでは、Visual Studio を確認できます。 機能、ドメイン固有言語およびそのソリューションを表示する方法と対話する必要があります。 Visual Studio 分離シェルの詳細については、次を参照してください。[分離シェルのカスタマイズ](https://vspartner.com/pages/vsshells)します。

Visual Studio Shell は、デプロイ ターゲットとして設定します。

1. **DslPackage**プロジェクトを開き、 **source.extension.tt**します。

2. `<SupportedProducts>`を挿入します。

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   置換*MyIsolatedShell*分離シェルのパッケージの名前に置き換えます。