---
title: 単体テスト作成用のコードの例
description: この記事では、Visual Studio で単体テストを使ってテストできるサンプル コードを提供します。
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: sample
helpviewer_keywords:
- unit test sample [Visual Studio]
- unit tests, samples
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93a6627b96daefa48c9a72fd84726775fc449bde
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704604"
---
# <a name="sample-code-for-testing"></a>テスト用のサンプル コード

このサンプル コードには、単体テストによってテストできるさまざまなメソッドとクラス (*BankAccount*) が含まれます。

このコードは、次のチュートリアルで使用されます。

- [マネージド コードの単体テストを作成し、実行する](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)。 このチュートリアルでは、単体テストの作成とカスタマイズ、実行、およびテスト結果の検討の手順について説明します。
- [コマンド ライン テスト ユーティリティを使用する](http://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867)。 このチュートリアルでは、MSTest.exe コマンドライン ユーティリティを使用してテストを実行し、結果を表示します。

## <a name="sample-code"></a>サンプル コード

このサンプルにある唯一の意図的なエラーは、Debit メソッドで、"m_balance += amount" の等号の前はプラス (+) ではなくマイナス (-) にする必要があるということです。

```csharp
using System;

namespace BankAccountNS
{
    /// <summary>
    /// Bank Account demo class.
    /// </summary>
    public class BankAccount
    {
        private string m_customerName;

        private double m_balance;

        private bool m_frozen = false;

        private BankAccount()
        {
        }

        public BankAccount(string customerName, double balance)
        {
            m_customerName = customerName;
            m_balance = balance;
        }

        public string CustomerName
        {
            get { return m_customerName; }
        }

        public double Balance
        {
            get { return m_balance; }
        }

        public void Debit(double amount)
        {
            if (m_frozen)
            {
                throw new Exception("Account frozen");
            }

            if (amount > m_balance)
            {
                throw new ArgumentOutOfRangeException("amount");
            }

            if (amount < 0)
            {
                throw new ArgumentOutOfRangeException("amount");
            }

            m_balance += amount; // intentionally incorrect code
        }

        public void Credit(double amount)
        {
            if (m_frozen)
            {
                throw new Exception("Account frozen");
            }

            if (amount < 0)
            {
                throw new ArgumentOutOfRangeException("amount");
            }

            m_balance += amount;
        }

        private void FreezeAccount()
        {
            m_frozen = true;
        }

        private void UnfreezeAccount()
        {
            m_frozen = false;
        }

        public static void Main()
        {
            BankAccount ba = new BankAccount("Mr. Bryan Walton", 11.99);

            ba.Credit(5.77);
            ba.Debit(11.22);
            Console.WriteLine("Current balance is ${0}", ba.Balance);
        }
    }
}
```

/* 例として登場する企業、組織、製品、ドメイン名、電子メール アドレス、ロゴ、人物、場所、およびイベントはすべて架空のものです。 実在する会社、組織、製品、ドメイン名、電子メールアドレス、ロゴ、人物、場所、イベントなどとは一切関係ありません。 \*/

## <a name="create-the-project"></a>プロジェクトの作成

このコードを操作するには、最初にプロジェクトを Visual Studio で作成します。 「[チュートリアル: マネージド コードの単体テストを作成し、実行する](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#create-a-project-to-test)」のプロジェクトを作成する手順に従います。

## <a name="see-also"></a>関連項目

- [チュートリアル: マネージド コードの単体テストを作成し、実行する](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)
- [チュートリアル: コマンド ライン テスト ユーティリティの使用](http://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867)
