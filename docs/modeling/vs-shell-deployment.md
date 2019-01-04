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
ms.openlocfilehash: 2d732b050a9f12b6324abaf253739cd4f3e223aa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914489"
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