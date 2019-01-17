---
title: '方法: 発行のバージョンに自動的にインクリメント ClickOnce |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b17a0c54ba0efa7a6eb732de45fa7d1644577041
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53861398"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>方法: ClickOnce の発行バージョンを自動的にインクリメントする

発行するときに、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]を変更するアプリケーション、`Publish Version`プロパティにより、アプリケーションの更新プログラムとして発行します。 既定では、Visual Studio が自動的にインクリメント、`Revision`の数、`Publish Version`アプリケーションを発行するたびにします。

この動作を無効にすることができます、**発行**のページ、**プロジェクト デザイナー**します。

> [!NOTE]
> 実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[リセット設定](../ide/environment-settings.md#reset-settings)」を参照してください。

## <a name="to-disable-automatically-incrementing-the-publish-version"></a>発行バージョンを自動的にインクリメントを無効にするには

1.  **ソリューション エクスプローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。

2.  **[発行]** タブをクリックします。

3.  **発行バージョン** セクションで、クリア、**リリースごとにリビジョンを自動的に**チェック ボックスをオンします。

## <a name="see-also"></a>関連項目

- [方法: ClickOnce の発行バージョンを設定する](../deployment/how-to-set-the-clickonce-publish-version.md)
- [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)
- [方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)