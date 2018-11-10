---
title: Azure をデバッグするためのオプションはクラウド サービス |Microsoft Docs
description: Azure cloud services のデバッグ
author: mikejo5000
manager: douge
ms.assetid: 80755da7-8350-4f5c-97ce-2962beabb36d
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 03/18/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.openlocfilehash: bd2608371871b7adc925fc11927fe061b00a1ec6
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002882"
---
# <a name="learn-the-various-ways-to-debug-an-azure-cloud-service"></a>Azure クラウド サービスをデバッグするためのさまざまな方法を理解する
この記事では、Azure クラウド サービスをデバッグするさまざまな方法へのリンクを提供します。 

## <a name="debugging-an-azure-cloud-service-in-visual-studio"></a>Visual Studio での Azure クラウド サービスのデバッグ
時間を節約でき、money、Azure を使用してコンピューティング エミュレーターは、ローカル コンピューターで、クラウド サービスをデバッグします。 展開する前に、サービスをローカルでデバッグ、コンピューティング時間に対して料金を支払うことがなくの信頼性とパフォーマンスを向上できます。 ただし、Azure でクラウド サービスを実行する場合にのみ、いくつかのエラーが発生する可能性があります。 Azure でクラウド サービスを実行するときにのみ発生するエラーは、サービスを発行するときにリモート デバッグとロール インスタンスにデバッガーをアタッチし、有効にしてデバッグできます。 詳細については、次を参照してください。[ローカル コンピューターに、クラウド サービスをデバッグ](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-your-cloud-service-on-your-local-computer)します。

## <a name="using-intellitrace"></a>IntelliTrace の使用 
.NET Framework 4.5 を対象とするロールを記述する Visual Studio Enterprise を使用する場合は、Visual Studio から Azure クラウド サービスを展開する時に IntelliTrace を有効にできます。 IntelliTrace では、Azure で実行されているかのようにアプリケーションをデバッグする Visual Studio で使用できるログを提供します。 詳細については、次を参照してください。 [IntelliTrace および Visual Studio で発行済みのクラウド サービスのデバッグ](http://go.microsoft.com/fwlink/p/?LinkId=623016)します。

## <a name="remote-debugging"></a>リモート デバッグ 
Visual Studio からクラウド サービスを展開する場合に、クラウド サービスにリモート デバッグを有効にすることができます。 展開用のリモート デバッグを有効にする場合は、リモート デバッグ サービスは、各ロール インスタンスを実行する仮想マシンにインストールされます。 などのこれらサービス`msvsmon.exe`- パフォーマンスに影響したりしないで余分なコストが発生します。 詳細については、次を参照してください。 [Azure でクラウド サービスのデバッグ](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-a-cloud-service-in-azure)します。

## <a name="next-steps"></a>次の手順
- [Visual Studio での VM または Azure クラウド サービスのデバッグ](./vs-azure-tools-debug-cloud-services-virtual-machines.md)-Azure クラウド サービスをデバッグする方法の詳細について説明します。