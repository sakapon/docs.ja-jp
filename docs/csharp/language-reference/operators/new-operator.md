---
description: new 演算子 - C# リファレンス
title: new 演算子 - C# リファレンス
ms.date: 06/25/2019
f1_keywords:
- new_CSharpKeyword
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 88ec929317d4e6c6651233c1a1aa0ce8a8cce611
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118274"
---
# <a name="new-operator-c-reference"></a>new 演算子 (C# リファレンス)

`new` 演算子は型の新しいインスタンスを作成します。

`new` キーワードは、[メンバーの宣言修飾子](../keywords/new-modifier.md)または[ジェネリック型制約](../keywords/new-constraint.md)として使用することもできます。

## <a name="constructor-invocation"></a>コンストラクターの呼び出し

型の新しいインスタンスを作成するには、通常は `new` 演算子を使用して、その型の[コンストラクター](../../programming-guide/classes-and-structs/constructors.md)の 1 つを呼び出します。

[!code-csharp-interactive[invoke constructor](snippets/shared/NewOperator.cs#Constructor)]

[オブジェクトまたはコレクション初期化子](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)を `new` 演算子と共に使用して、1 つのステートメント内でオブジェクトのインスタンス化と初期化を行うことができます。次に例を示します。

[!code-csharp-interactive[constructor with initializer](snippets/shared/NewOperator.cs#ConstructorWithInitializer)]

## <a name="array-creation"></a>配列の作成

`new` 演算子を使用して配列インスタンスを作成することもできます。次に例を示します。

[!code-csharp-interactive[create array](snippets/shared/NewOperator.cs#Array)]

1 つのステートメント内で配列の初期化構文を使用して配列インスタンスを作成し、そこに要素を設定します。 次の例に、これを行うためのさまざまな方法を示します。

[!code-csharp-interactive[initialize array](snippets/shared/NewOperator.cs#ArrayInitialization)]

配列の詳細については、「[配列](../../programming-guide/arrays/index.md)」を参照してください。

## <a name="instantiation-of-anonymous-types"></a>匿名型のインスタンス化

[匿名型](../../programming-guide/classes-and-structs/anonymous-types.md)のインスタンスを作成するには、`new` 演算子とオブジェクト初期化子構文を使用します。

[!code-csharp-interactive[anonymous type](snippets/shared/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a>型のインスタンスの破棄

以前作成した型のインスタンスを破棄する必要はありません。 参照型と値型のインスタンスは両方とも自動的に破棄されます。 値型のインスタンスは、それらを格納しているコンテキストが破棄されるとすぐに破棄されます。 参照型のインスタンスは[ガベージ コレクター](../../../standard/garbage-collection/index.md)によって、そのインスタンスへの最後の参照が削除された後、不特定のタイミングで破棄されます。

ファイル ハンドルなどのアンマネージド リソースを含む型インスタンスの場合、格納されているリソースができるだけ早く確実に解放されるように、決定的なクリーンアップを使用することをお勧めします。 詳細については、<xref:System.IDisposable?displayProperty=nameWithType> API リファレンスと [using ステートメント](../keywords/using-statement.md)に関する記事を参照してください。

## <a name="operator-overloadability"></a>演算子のオーバーロード可/不可

ユーザー定義型は `new` 演算子をオーバーロードできません。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、[C# 言語仕様](~/_csharplang/spec/introduction.md)の [new 演算子](~/_csharplang/spec/expressions.md#the-new-operator)に関するセクションを参照してください。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# の演算子と式](index.md)
- [オブジェクト初期化子とコレクション初期化子](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
