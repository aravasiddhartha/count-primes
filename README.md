class Solution(object):
    def countPrimes(self, n):
        """
        :type n: int
        :rtype: int
        """
        if n < 3:
            return 0  # No primes less than 2

        is_prime = [True] * n
        is_prime[0] = is_prime[1] = False  # 0 and 1 are not prime

        # Only need to check factors up to sqrt(n)
        i = 2
        while i * i < n:
            if is_prime[i]:
                # Mark all multiples of i starting from i*i as False
                for j in range(i * i, n, i):
                    is_prime[j] = False
            i += 1

        # Count remaining True values
        return sum(is_prime)
        
